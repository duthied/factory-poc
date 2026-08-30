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
5. Dispatch the first outstanding chunk (see Loop).

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
     Retries (a mechanical bounce still counts toward the cap). If Retries ≥ 3 →
     `needs-human`; else set `rejected` with the exact failing check + offending
     lines in Notes and loop back to step 1 for a rewrite.
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
   - `FAIL` → increment Retries. If Retries ≥ 3 → set `needs-human`, pause, and
     tell the human. Else set `rejected` with the reason in Notes and loop back
     to step 1 for a rewrite.

6. Update `../state/progress.md` after every transition. Go to step 1.

## Finish

When target met and all chunks `approved`:
1. Set Run status to `assembling` in `progress.md`.
2. Dispatch the builder. If a `builder` session is running, `SendMessage` it;
   otherwise spawn one with the `Agent` tool or tell the human to start a
   session in `builder/`. Message:
   > "Assemble the approved chunks. Read `builder/CLAUDE.md`, `spec.md` §6, and
   > `state/progress.md`. Reply when the deliverable is in `output/`."
3. On the builder's reply, set Run status `complete` and report the output path
   to the human.

## Rules

- Keep messages small — a pointer and a brief, never chunk text.
- Dispatch one chunk at a time; do not let two chunks be in-flight at once
  (keeps `progress.md` unambiguous and the writer/reviewer focused).
- If a reply never comes or a session is unreachable, note it in `progress.md`
  and tell the human — don't silently retry forever.
