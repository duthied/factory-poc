# Software Factory — Long-Form Prose

A multi-agent "factory" that produces one large piece of long-form prose (a
book / report / narrative) defined by `spec.md`, built up chunk by chunk until
it hits the target length in the spec.

This root file holds **shared conventions only**. Each agent's role-specific
steering lives in its own folder (`orchestrator/`, `writer/`, `reviewer/`,
`builder/`) so that a session running in one folder does not inherit another
role's context.

## The agents

| Role | Runs in | Job |
|------|---------|-----|
| **Orchestrator** | `orchestrator/` | Owns state. Decides what to write next, dispatches work, tracks progress against the spec target, drives the loop. The only writer of `state/progress.md`. |
| **Writer** | `writer/` | Writes one chunk at a time when asked, saves it to `chunks/`, reports back. |
| **Reviewer** | `reviewer/` | Checks a chunk against the spec. Records a verdict; logs reusable problems to `learnings.md`. |
| **Builder** | `builder/` | Once all chunks are approved and the target is met, assembles them into the final deliverable in `output/`. Runs once, on demand. |
| **Evaluator** | `evaluator/` | After the builder assembles, judges the *whole* deliverable against the spec's rubric (`spec.md` §9), scores it, and writes `state/eval-report.md`. A failing eval sends specific chunks back for revision. Runs once per evaluation round. |

## Two channels: messages vs. files

The agents are **separate live Claude sessions** that coordinate two ways:

- **Messages (`SendMessage`) = control/notifications.** Small: "write chunk 02",
  "chunk ready", "review passed". Carry a *pointer + one-line brief*, never a
  chunk body.
- **Files = data + durable state.** The chunk text, spec, progress, review log,
  and learnings all live on disk. If a session dies, the files are the source of
  truth and the run can resume from them.

**Never paste chunk bodies into messages.** Reference the file path. This keeps
each agent's context lean and roles isolated.

## Shared state files

| File | Owner (only writer) | Everyone else |
|------|--------------------|----------------|
| `spec.md` | human | read-only |
| `state/progress.md` | **orchestrator** | read-only |
| `state/review-log.md` | reviewer (append-only) | read-only |
| `state/learnings.md` | reviewer (append-only) | writer reads before writing |
| `chunks/chunk-NN.md` | writer (one file per chunk) | reviewer/builder read |
| `output/` | builder | evaluator reads |
| `state/eval-report.md` | evaluator (append per round) | orchestrator reads |

Single-writer discipline avoids three sessions racing on the same file.
Append-only files (`review-log.md`, `learnings.md`) are safe for concurrent
appends.

## Chunk lifecycle

```
queued-for-writing → written → [mechanical gates §5a] → queued-for-review → approved
        ↑                              │ fail (auto-bounce)        │ fail          (stamped
        └──────────────────────────────┴───── rejected ───────────┘            with Spec-ver)
                              (retry count++; learnings appended on editorial fail)
```

Chunks clear the deterministic **mechanical gates (spec §5a)** — length,
em/en-dashes, prose-only, UK spelling — which the orchestrator runs itself
*before* spending a reviewer turn; a mechanical failure bounces straight back to
the writer. Only chunks that pass the gates reach the reviewer for **editorial
judgment (§5b)**. On approval the chunk is stamped with the current
**Spec-Version**; if the spec later changes and its version is bumped, the
orchestrator flags older-stamped chunks as stale on startup and re-queues them.

Only the **orchestrator** advances a chunk between phases, based on the replies
it receives. Writer and reviewer report results; they do not change status.

## Messaging protocol (summary)

1. Orchestrator → Writer: "Write chunk NN. Brief: … Read `spec.md`, your
   `progress.md` row, `state/learnings.md`. Save to `chunks/chunk-NN.md`. Reply
   to me (the sender) with the word count when done."
2. Writer → Orchestrator: "chunk-NN.md written, NNNN words."
3. Orchestrator → Reviewer: "Review `chunks/chunk-NN.md` against `spec.md`.
   Reply pass/fail. On fail, append the reusable problem to
   `state/learnings.md` and the verdict to `state/review-log.md`."
4. Reviewer → Orchestrator: "chunk-NN: PASS" or "chunk-NN: FAIL — <reason>".
5. Orchestrator updates `progress.md` and either dispatches the next chunk or,
   when target met and all approved, tells the builder to assemble.
6. After assembly the orchestrator dispatches the evaluator, which scores the
   whole deliverable (`spec.md` §9) into `state/eval-report.md`. A PASS finishes
   the run; a FAIL sends the implicated chunks back through the loop and
   re-evaluates (up to 2 rounds, then `needs-human`).

Every message names its sender and asks the recipient to **reply to sender**, so
no one hardcodes another session's (dynamic) name.

## Running the factory

1. Fill in `spec.md` with the real story spec and target length.
2. Start (or reuse) sessions in `writer/`, `reviewer/`, and, at the end,
   `builder/` and `evaluator/` (or let the orchestrator spawn those two as
   subagents). The orchestrator session is the driver.
3. In the orchestrator session, say "begin" — it reads the spec, seeds
   `progress.md` from the outline, and starts dispatching.
4. Watch `state/progress.md` for live status.

## Conventions

- Chunk files: `chunks/chunk-NN.md`, zero-padded, in reading order.
- Word counts are the unit of "length" tracked against the spec target.
- Retry cap: a chunk that fails review **3** times is marked `needs-human` in
  `progress.md` instead of looping forever.
- Keep `learnings.md` to *reusable* guidance ("avoid X", "the spec wants Y"),
  not one-off nitpicks.
