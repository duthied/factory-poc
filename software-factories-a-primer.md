# What's a "software factory"? (a 2-minute tour)

A **software factory** is an assembly line of AI agents, each with one job, that
together build something too big for a single prompt to do well. Instead of
asking one model to "write the whole thing," you split the work into chunks and
let specialized agents write, check, assemble, and grade them, coordinating
through shared files on disk.

This repo is a working POC. The "product" is a 10,000-word story, but the pattern
is general.

## The parts

- **Orchestrator** — the foreman. Owns the state, decides what's next, runs cheap
  checks, and drives the loop.
- **Writer** — produces one chunk at a time.
- **Reviewer** — judges each chunk against the spec.
- **Builder** — assembles approved chunks into the finished whole.
- **Evaluator** — grades the *whole* against a rubric (things you can't see one
  chunk at a time).

They talk through small **messages** (control) and durable **files** (the data:
spec, progress, logs, chunks). The spec is the contract everyone answers to.

## Techniques that show up in most factories

- **Spec-driven** work with a single source of truth.
- **Separation of concerns** — each agent runs isolated so contexts don't bleed.
- **Deterministic gates before expensive judgment** — cheap mechanical checks
  (length, formatting, banned patterns) run first; the LLM reviewer only sees
  clean work.
- **A holistic evaluator** with a scored rubric, plus a **feedback loop**: failures
  become durable "learnings" that get promoted into the spec.
- **Self-recovery** (a polling heartbeat, so a dropped message doesn't stall the
  line) and **per-run metrics** so you can see whether it's improving.

## Did it work?

Yes, and measurably. Run 01 scored 4.4/5. We read the eval, **codified the
findings into the spec** (a reveal ledger, explicit canon, a whole-work quality
gate), and re-ran: **4.71/5**, with two dimensions rising from 4 to 5 and zero
stalls. The honest footnote: rules fixed things cleanly; a raw count-threshold got
gamed (the model just renamed the tic). Good factories measure their own misses.

## Would this build *software* instead of stories?

The mapping is almost one-to-one:

| Story factory | Software factory |
|---|---|
| chunk of prose | module / feature / PR |
| mechanical gates (dashes, length) | linters, type-checks, formatters |
| editorial review | code review |
| whole-work evaluator | integration/e2e tests, acceptance criteria |
| canon (fixed facts) | architecture invariants & interfaces |
| spec versioning | changing requirements |

The lesson transfers too: **deterministic checks catch far more, far cheaper,
than a smart reviewer re-reading everything** — which is exactly how good
engineering pipelines already work. The factory just wires an agent to each stage.
