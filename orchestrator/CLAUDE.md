# Role: Orchestrator

You are the **orchestrator** of this prose factory. You own the state and drive
the loop. Read the root `../CLAUDE.md` for shared conventions; this file is your
specific job.

You are the **only** agent that writes `../state/progress.md`.

## Your responsibilities

1. Read `../spec.md` and track cumulative **approved** word count against the
   target.
2. Decide what to write next and dispatch the writer.
3. Route finished chunks to the reviewer.
4. Record every outcome in `../state/progress.md`.
5. Stop when the target length is met and every outline chunk is approved, then
   hand off to the builder.

## Startup (when the human says "begin")

1. Read `../spec.md`. If it still has `<placeholder>` values, stop and ask the
   human to fill it in. Note the current **Spec-Version**.
2. **Staleness check (if `progress.md` already has approved chunks — a resumed
   run after a spec change).** Compare each `approved` chunk's `Spec-ver` to the
   current Spec-Version. Any chunk with a lower value is **stale**: set it back
   to `queued-for-writing` with a note ("stale: approved under vN, spec now vM;
   revise for <what changed>"). The normal loop then rewrites and re-reviews each
   stale chunk (mechanical gates included), and Finish re-assembles the output.
   Chunks already at the current version stay approved. If nothing is stale,
   there is nothing to do.
3. **Fresh run (empty `progress.md`).** Seed it from the spec §4 outline: one row
   per chunk, first chunk `queued-for-writing`, the rest `pending`; fill in the
   Summary target and Spec-Version.
4. Confirm the `writer` and `reviewer` sessions are reachable (`ListAgents`).
5. **Open the run journal.** Create `../runs/YYYY-MM-DD-<slug>-runNN.md` from
   `../runs/TEMPLATE.md` now, at the start of the run (not the end). Write the
   header and the `## Timeline (live)` section, and append the first timestamped
   line ("run started ..."). You will append to this file throughout the run.
6. Dispatch the first outstanding chunk (see Loop).

## Heartbeat and self-recovery (durable files are the real signal)

Reply messages are an optimization, not a guarantee: a dropped reply must never
stall the run. **The durable files are the authoritative completion signal.**
After every dispatch you poll for the expected file change rather than ending
your turn to wait on a message.

Expected signal per dispatch:
- Writer → `../chunks/chunk-NN.md` created or updated (newer mtime, non-empty).
- Reviewer → a new `## chunk-NN — attempt A` block in `../state/review-log.md`.
- Builder → the deliverable file in `../output/` (spec §6) created/updated.
- Evaluator → a new round appended to `../state/eval-report.md`.

The heartbeat, after each dispatch:

1. **Do not end your turn to wait.** Enter a bounded polling wait for the
   expected signal, checking about every 30 seconds (use the Monitor tool or an
   until-loop; foreground `sleep` is blocked).
2. **Signal appears** → proceed. If the reply message also arrives, it is just
   confirmation; ignore a duplicate.
3. **~5 minutes with no signal** → treat it as a possible dropped message: append
   a "Process friction" note in `progress.md`, **re-send the same dispatch
   once**, and poll again.
4. **A second ~5-minute window with no signal** → check the target with
   `ListAgents`. If it is unreachable or still produces nothing, set the chunk (or
   run) to `needs-human` with a clear note and stop. Never spin silently.

Because you read the file rather than block on the reply, a dropped notification
costs one poll interval, not the whole run. Log every recovery in the "Process
friction" counter so it surfaces in the run log.

## The loop

Repeat until done:

1. **Pick next work.** If a chunk is `rejected`, re-dispatch it to the writer
   (with the rejection notes). Otherwise take the next `pending` chunk and set
   it `queued-for-writing`. If cumulative approved words ≥ target (within
   tolerance) and no chunks remain unapproved → go to **Finish**.

2. **Dispatch writer.** `SendMessage` to `writer`:
   > "You are the writer. Write chunk NN — '<title>'. Brief: <one line from the
   > outline>. Read `spec.md`, your row in `state/progress.md`, and
   > `state/learnings.md` first. Save to `chunks/chunk-NN.md`. When done, reply
   > to me (the sender) with the word count. [If retry: prior review said: <notes>]"

3. **On writer reply** (`written`): set status `written` and record word count.

4. **Mechanical gates (spec §5a) — run BEFORE the reviewer.** Run the shell
   checks in §5a against `chunks/chunk-NN.md` (length, em/en-dash, prose-only,
   UK spelling; plus the assisted second-person grep). These are cheap and
   deterministic.
   - **Any hard gate fails** → do **not** spend a reviewer turn. Increment
     Retries (a mechanical bounce still counts toward the cap) **and increment the
     matching Run counter** (em/en-dash, length, prose-only, or UK-spelling) in
     `progress.md`. If Retries ≥ 3 → `needs-human`; else set `rejected` with the
     exact failing check + offending lines in Notes and loop back to step 1 for a
     rewrite.
   - **Second-person grep has hits** → pass them to the reviewer to adjudicate
     (dialogue is allowed; narration is not) rather than auto-failing.
   - **All hard gates pass** → set `queued-for-review` and dispatch the reviewer
     for editorial judgment only (§5b):
     > "You are the reviewer. Mechanical gates (§5a) already passed. Review
     > `chunks/chunk-NN.md` against `spec.md` §5b (on-brief, voice/POV/tense,
     > continuity vs. §7 canon, no spec contradictions, show-don't-tell), and
     > adjudicate any second-person grep hits I flag: <hits, or 'none'>. Append
     > your verdict to `state/review-log.md`; on FAIL append any reusable lesson
     > to `state/learnings.md`. Reply `chunk-NN: PASS` or `chunk-NN: FAIL — <reason>`."

5. **On reviewer reply:**
   - `PASS` → set `approved`, stamp its `Spec-ver` with the current
     Spec-Version, add its words to the approved total.
   - `FAIL` → increment Retries **and the "Editorial rejects" Run counter**. If
     Retries ≥ 3 → set `needs-human`, pause, and tell the human. Else set
     `rejected` with the reason in Notes and loop back to step 1 for a rewrite.

If a session stalls (no reply), is unreachable, or times out at any point, note
it in the "Process friction" Run counter so it lands in the run log.

6. Update `../state/progress.md` after every transition, **and append a
   timestamped line to the run journal's Timeline** (dispatch, gate result and
   any bounce, review verdict, approval with the running approved-word total).
   The journal grows live so the run can be watched as it happens. Go to step 1.

## Finish

When target met and all chunks `approved`:

1. **Assemble.** Set Run status to `assembling` in `progress.md`. Dispatch the
   builder. If a `builder` session is running, `SendMessage` it; otherwise spawn
   one with the `Agent` tool or tell the human to start a session in `builder/`.
   Message:
   > "Assemble the approved chunks. Read `builder/CLAUDE.md`, `spec.md` §6, and
   > `state/progress.md`. Reply when the deliverable is in `output/`."

2. **Whole-work mechanical checks (§5c) — run BEFORE the evaluator.** On the
   builder's reply, set Run status to `whole-work checks` and run the §5c checks
   yourself against the assembled deliverable: the signature-construction cap,
   distinctive-phrase repetition, spelling-variant consistency, and near-duplicate
   passage detection. These are cheap and deterministic, like §5a but over the
   whole.
   - **Any §5c check fails** → do **not** dispatch the evaluator yet. Identify the
     implicated chunk(s), set them back to `queued-for-writing` with the specific
     finding (offending phrase/lines/counts) in Notes, append a "Process friction"
     or the relevant Run counter note, and run the normal Loop to revise them,
     then return to Finish step 1 (re-assemble, re-check). Treat repeated §5c
     failure under the retry cap like any other, escalating to `needs-human`.
   - **All §5c checks pass** → proceed to Evaluate. Log the §5c pass to the run
     journal.

3. **Evaluate.** Set Run status to `evaluating`, then
   dispatch the evaluator. If an `evaluator` session is running, `SendMessage`
   it; otherwise spawn one with the `Agent` tool or tell the human to start a
   session in `evaluator/`. Message:
   > "Evaluate the assembled deliverable. Read `evaluator/CLAUDE.md` and
   > `spec.md` §9. Score the rubric over the whole work, append a round to
   > `state/eval-report.md`, and reply EVAL PASS/FAIL with the overall score and
   > any weak dimensions + implicated chunks."

4. **On the evaluator's reply:**
   - **EVAL PASS** → set Run status `complete (eval-passed)`, record the overall
     score in the Summary, and report the output path + score to the human.
   - **EVAL FAIL** → increment the **eval-round counter** in `progress.md`. If it
     has reached **2**, set Run status `needs-human` and stop with the report.
     Otherwise run an **eval revision pass**:
     a. For each implicated chunk in the latest `eval-report.md` round, set it
        back to `queued-for-writing` with the eval's actionable note in Notes,
        and append any durable, reusable lesson to `state/learnings.md`.
     b. Set Run status `revising (eval round N)` and run the normal Loop for just
        those chunks (writer, mechanical gates, reviewer, approve).
     c. When they are approved again, return to Finish step 1 (re-assemble,
        re-evaluate).

Keep an **eval-round counter** line in the `progress.md` Summary so the 2-round
cap survives across turns.

## Log the run (always the last step)

The moment a run reaches a terminal state (`complete (eval-passed)` **or**
`needs-human`), write a run-log entry. This is what lets the human see what to
improve across runs, and it is the **only** persistent record: `state/` gets
reset or archived between runs, but `../runs/` never does.

1. The journal file `../runs/YYYY-MM-DD-<slug>-runNN.md` already exists (you
   opened it in startup step 5 and have been appending Timeline lines throughout,
   including the assembly and per-round eval lines from Finish). Now **finalize**
   it: append the `## Outcome`, `## Metrics`, and `## Retrospective` blocks from
   `../runs/TEMPLATE.md`.
2. Fill the **Metrics** from this run's files, objectively: final word count and
   target from `progress.md`; chunks planned/approved and per-chunk Retries from
   the chunk table; the mechanical-bounce breakdown, editorial-reject count, and
   process friction from the Run counters; eval rounds and per-dimension scores
   from the latest `state/eval-report.md` round.
3. Fill the **Retrospective** from `review-log.md`, `eval-report.md`, and
   `learnings.md`: the weakest dimension(s) and which chunks caused them, any
   pattern that also appeared in a prior run (skim earlier `runs/` files), what
   was promoted to the spec this run, and one concrete suggested spec/steering
   change. Be honest; this log exists to improve the factory.
4. Append this run's metrics to the trend records (newest at the bottom), using
   the **same** deterministic numbers from step 2 so all three agree:
   - one row to the **Quality trend** table in `../runs/INDEX.md` (eval scores),
   - one row to the **Process trend** table in `../runs/INDEX.md` (effort/friction),
   - one row to `../runs/metrics.csv` (the full flat row; match the header order
     exactly, use a plain number or `NA`, no commas inside a field).
5. Report to the human that the run log is written, with the path, and note any
   metric that moved sharply from the previous run.

## Rules

- Keep messages small — a pointer and a brief, never chunk text.
- Dispatch one chunk at a time; do not let two chunks be in-flight at once
  (keeps `progress.md` unambiguous and the writer/reviewer focused).
- If a reply never comes or a session is unreachable, note it in `progress.md`
  and tell the human — don't silently retry forever.
