# Software Factory (POC)

A small proof-of-concept for producing one large piece of **long-form prose** (a
book, report, or narrative) with a team of cooperating AI agents instead of a
single monolithic prompt. A spec defines the target; the factory writes, reviews,
and assembles the work chunk by chunk until it hits that target.

It is deliberately file-first and model-agnostic: the coordination lives in plain
markdown files on disk, so a run is inspectable, resumable, and diffable in git.

## The idea

One long deliverable is hard to generate well in a single pass. So the work is
broken into **chunks** (roughly chapter- or section-sized), and four specialised
agents each do one job:

| Agent | Job |
|-------|-----|
| **Orchestrator** | Owns the state. Decides what to write next, dispatches work, runs the cheap mechanical checks, tracks progress against the spec's target, and drives the loop. The only writer of `state/progress.md`. |
| **Writer** | Writes (or revises) one chunk at a time when asked, saves it to `chunks/`, and reports back. |
| **Reviewer** | Judges a chunk against the spec's editorial criteria, records a verdict, and logs reusable lessons. |
| **Builder** | Once every chunk is approved and the target is met, assembles the chunks into the final deliverable in `output/`. Runs once, at the end. |
| **Evaluator** | Judges the *whole* assembled deliverable against a spec-defined rubric (arc, sustained ambiguity, voice consistency, pacing, prose, coda, themes), scores each dimension, and writes `state/eval-report.md`. A failing eval sends specific chunks back for revision. |

Each agent is a **separate Claude session** running in its own folder, so it loads
only its own role steering and does not inherit another role's context.

## How it works

### Two channels: messages vs. files

The agents coordinate two ways, and keeping them separate is the core design idea:

- **Messages (`SendMessage`) = control / notifications.** Small: "write chunk 02",
  "chunk ready", "PASS". A message carries a *pointer and a one-line brief*, never
  a chunk's text.
- **Files = data and durable state.** The chunk prose, the spec, the progress
  table, the review log, and the learnings all live on disk. If a session dies,
  the files are the source of truth and a run resumes from them.

This keeps each agent's context lean and its role isolated, and it means you can
watch (or audit) an entire run just by reading the files.

### The chunk lifecycle

```
queued-for-writing → written → [mechanical gates §5a] → queued-for-review → approved
        ↑                              │ fail (auto-bounce)        │ fail          (stamped
        └──────────────────────────────┴───── rejected ───────────┘            with Spec-ver)
                              (retry count++; learnings appended on editorial fail)
```

1. The **orchestrator** picks the next chunk from the spec outline and asks the
   **writer** to write it.
2. The **writer** writes `chunks/chunk-NN.md` and replies with the word count.
3. The **orchestrator** runs the **mechanical gates** (`spec.md` §5a) itself:
   deterministic shell checks for length, em/en-dashes, prose-only formatting,
   and UK spelling. A failure bounces straight back to the writer **without
   spending a reviewer turn**.
4. Chunks that pass the gates go to the **reviewer** for **editorial judgment**
   (`spec.md` §5b): on-brief, voice/POV/tense, continuity, show-don't-tell.
   - **PASS** → the orchestrator marks it `approved`, stamps it with the current
     Spec-Version, and adds its words to the running total.
   - **FAIL** → the reviewer logs the problem to `state/review-log.md` and any
     reusable rule to `state/learnings.md`; the chunk is re-queued for a rewrite.
     After 3 failures it is flagged `needs-human`.
5. When cumulative approved words reach the target and every chunk is approved,
   the **builder** assembles them into `output/`.
6. The **evaluator** then judges the assembled whole against the spec's rubric
   (`spec.md` §9), scoring each dimension 1 to 5 into `state/eval-report.md`. A
   **PASS** (overall mean at least 4.0 and no dimension below 3) finishes the
   run; a **FAIL** names the specific chunks behind each weak dimension, which
   the orchestrator re-queues for revision before re-assembling and
   re-evaluating (up to two rounds, then it stops for a human).

Only the orchestrator moves a chunk between phases, so three live sessions never
race on `state/progress.md`. The append-only logs (`review-log.md`,
`learnings.md`) are safe for concurrent writes.

### Spec versioning and staleness

`spec.md` carries a **Spec-Version**. Each approved chunk is stamped with the
version it was approved under. When a rule that affects already-written prose
changes (voice, length, style, canon), you bump the Spec-Version; on its next
startup the orchestrator flags any chunk stamped with an older version as
**stale** and re-queues it for a revision pass. This is how a spec change (for
example, "never use em-dashes") propagates back through work that was already
finished.

### Learnings and canon

- **`state/learnings.md`** is a short, working list of active guidance the writer
  reads before each chunk. When a lesson proves durable it is *promoted* into the
  spec (a style rule in §3, or a fixed fact in §7 Canon), the Spec-Version is
  bumped, and the learning is cleared. This keeps the writer's context from
  bloating over a long run.
- **`spec.md` §7 Canon** is the growing list of fixed facts (characters, timeline,
  recurring images) so continuity does not depend on re-reading every prior chunk.

### The run log

`state/` describes the *current* run and is reset or archived when a new run
starts, so it cannot tell you whether the factory is improving. The **`runs/`**
directory fills that gap: it is persistent and never reset. The orchestrator
opens a per-run file `runs/YYYY-MM-DD-<slug>-runNN.md` at the *start* of the run
and appends a timestamped line to its `## Timeline` at every transition, so it
can be read mid-run to watch progress. At completion it finalizes that same file
with two more parts:

- **Deterministic metrics** drawn from the run's own files: final word count vs.
  target, chunks planned/approved, total rewrites broken down into mechanical
  gate bounces (by type) versus editorial rejects, per-chunk retries, eval rounds
  used, the eval score per dimension, and any process friction (stalls,
  unreachable agents).
- **A short retrospective**: the weakest dimension and which chunks caused it,
  any pattern recurring from earlier runs, what was promoted into the spec, and
  one concrete suggested improvement.

To see the metrics change run over run, the orchestrator also appends the
numbers to two trend records each run:

- **`runs/INDEX.md`** holds two human-readable matrices, one row per run: a
  **Quality trend** (the seven eval scores + overall) and a **Process trend**
  (rewrites, mechanical bounces by type, editorial rejects, eval rounds,
  friction). Read down any column to watch that metric move across runs.
- **`runs/metrics.csv`** is the same data as one flat row per run, machine
  readable for sorting, diffing, or charting a metric over time.

The per-run markdown files carry the narrative retrospective; the matrices and
CSV carry the numbers over time. Together they are what you read when deciding
what to change about the spec or the agents' steering.

## Layout

```
factory-poc/
├── CLAUDE.md              # Shared conventions, agent roster, lifecycle
├── spec.md               # The spec: target length, voice, outline, acceptance criteria, canon
├── state/
│   ├── progress.md       # Coordination bus + per-chunk status (orchestrator-owned)
│   ├── review-log.md     # Append-only reviewer verdicts
│   ├── learnings.md      # Append-only working guidance for the writer
│   └── eval-report.md    # Append-per-round holistic scores (evaluator-owned)
├── chunks/               # chunk-NN.md written here (writer)
├── output/               # Final assembled deliverable (builder)
├── runs/                 # Persistent per-run log (metrics + retrospective) + INDEX.md
├── archive/              # Superseded runs (e.g. v2-literary/), preserved
├── orchestrator/CLAUDE.md
├── writer/CLAUDE.md
├── reviewer/CLAUDE.md
├── builder/CLAUDE.md
└── evaluator/CLAUDE.md
```

Because Claude Code loads `CLAUDE.md` files from the current directory up the
tree, a session started in `writer/` loads the shared root plus the writer's
role steering, and nothing else. That is the context isolation.

## Running it

1. **Fill in `spec.md`** with the real work: title, target length, voice, the
   chunk outline (§4), the acceptance criteria (§5), and assembly rules (§6).
2. **Start the agent sessions.** Open a Claude session in `writer/` and one in
   `reviewer/` (and, at the end, `builder/` and `evaluator/` — or let the
   orchestrator spawn those two as subagents). The orchestrator session is the
   driver.
3. **Tell the orchestrator "begin".** It validates the spec, seeds
   `state/progress.md` from the outline, confirms the writer and reviewer are
   reachable, and dispatches the first chunk.
4. **Watch `state/progress.md`** for live status, and the chunk files as they
   land.

To make a spec change ripple through finished work, edit `spec.md`, bump the
**Spec-Version**, and tell the orchestrator "begin" again — the staleness check
re-queues the affected chunks.

## The included sample run

The repo ships with a completed run so you can see the whole pipeline exercised:
**"The Lighthouse at Kestrel Point,"** a ~3,139-word literary short story in three
chunks, assembled in `output/the-lighthouse-at-kestrel-point.md`. The
`state/review-log.md` records the real history, including a chunk that failed
review (a timeline contradiction and a second-person breach), the lessons that
were logged, and the rewrite that passed — plus a later spec change (banning
em-dashes) that triggered a revision pass across all three chunks.

## Status and limitations

This is a POC. Known rough edges, roughly in priority order:

- **The notification channel is a convenience, not a dependency.** Reply
  messages between agents can be dropped, so the orchestrator treats the
  **durable files as the authoritative completion signal**: after each dispatch
  it polls for the expected file change (the written chunk, a new review-log
  verdict, the assembled output, a new eval round) with a heartbeat, re-dispatches
  once on a timeout, and escalates to `needs-human` rather than stalling. A
  dropped notification costs one poll interval, not the run. (This was added
  after a real run stalled ~13 minutes on a dropped review reply.)
- **`state/progress.md` is hand-edited markdown.** A JSON source of truth with a
  rendered markdown view would be less brittle across sessions.
- **Continuity relies partly on re-reading prior chunks.** The §7 canon reduces
  this, but a full "story bible" maintained after each approval is what a
  50-chunk book would need.
- **Serial by design.** One chunk is in flight at a time to keep state
  unambiguous; parallel chunks would need a locking convention.
