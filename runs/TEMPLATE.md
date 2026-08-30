# Run entry template

The orchestrator copies this into `runs/YYYY-MM-DD-<slug>-runNN.md` at run
completion and fills it in. One file per run, immutable once written. `<slug>` is
a short name for the work (e.g. `lighthouse`); `NN` increments per work.

Draw the **metrics** from the run's own files (`state/progress.md` run counters,
`state/review-log.md`, `state/eval-report.md`) so they are objective. Draw the
**retrospective** from the same files plus `state/learnings.md`. Keep it honest;
this log exists to improve the factory, not to flatter a run.

The file is a **live journal**: the orchestrator creates it at run start with the
Timeline section and appends a timestamped line at every transition, then adds
the Outcome / Metrics / Retrospective blocks at completion. So it can be read
mid-run to watch progress, and ends as the full record.

---

# Run YYYY-MM-DD — <slug> — Spec-Version V — run NN

## Timeline (live; appended at every transition)

```
HH:MM  run started (Spec-Version V, target NNNN)
HH:MM  chunk NN dispatched to writer
HH:MM  chunk NN written, NNNN words
HH:MM  chunk NN §5a gates: pass | BOUNCE <type> (counter++)
HH:MM  chunk NN review: PASS | FAIL <reason>
HH:MM  chunk NN approved (approved total NNNN / target)
HH:MM  all chunks approved; builder assembling
HH:MM  eval round R: <dim scores>; verdict PASS|FAIL
HH:MM  run complete | needs-human
```

## Outcome
- Deliverable: `output/<file>.md` (NNNN words / <target> target, within/outside tolerance)
- Final status: `complete (eval-passed)` | `needs-human`
- Eval verdict: PASS | FAIL, overall X.X / 5 (round R of 2)

## Metrics (deterministic)
- Chunks: N planned, N approved
- Total rewrites: N  (mechanical bounces: N, editorial rejects: N)
- Retries by chunk: ch0N=N, ch0N=N, ... (only chunks that needed >0)
- Mechanical gate bounces by type: em/en-dash=N, length=N, prose-only=N, UK-spelling=N, second-person=N
- Eval rounds used: R of 2
- Eval scores: arc=N, ambiguity=N, voice=N, pacing=N, prose=N, coda=N, themes=N
- Process friction: <silent-turn stalls, unreachable agents, timeouts; or "none">

## Retrospective (what to improve)
- Weakest dimension(s): <dimension (score)> — <which chunks, why>
- Recurring pattern: <problem that also appeared in a prior run, if any>
- Learnings promoted to spec this run: <what, or "none">
- Suggested spec/steering change: <concrete, actionable; or "none">
