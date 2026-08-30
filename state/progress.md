# Progress — coordination bus

**Owner: orchestrator only.** All other agents read this file; only the
orchestrator changes status. Seeded from `spec.md` §4 at the start of a run.

## Summary

- **Spec-Version:** 3
- **Target:** 10,000 words (plus or minus 10%)
- **Approved so far:** 9709 words
- **Run status:** complete (eval-passed)
- **Eval rounds used:** 1 of 2
- **Latest eval:** Round 1 PASS — overall 4.4 / 5, no dimension below 4 (see `state/eval-report.md`)

### Run counters (orchestrator maintains during the run; dumped into the run log at completion)

- Mechanical-gate bounces by type: em/en-dash 0, length 0, prose-only 0, UK-spelling 0, second-person 0
- Editorial rejects (reviewer FAIL): 1
- Process friction: 1 — silent stall ~13 min on chunk-04: reviewer's PASS reply dropped; recovered from state/review-log.md (durable source of truth)

The per-chunk `Retries` column already records total rewrites per chunk; these
counters break that total down by cause for the run log.

`Spec-ver` records the Spec-Version each chunk was approved under. On startup the
orchestrator compares it to the current Spec-Version; any `approved` chunk with a
lower value is stale and gets re-queued for a revision pass.

## Chunks

| # | Title | Status | Words | Retries | Spec-ver | Notes |
|---|-------|--------|-------|---------|----------|-------|
| 01 | The Road Back | approved | 1098 | 0 | 3 | passed §5a + §5b |
| 02 | The Keeper's Room | approved | 1071 | 1 | 3 | passed on rewrite (canon fix) |
| 03 | The Ledger | approved | 953 | 0 | 3 | passed §5a + §5b |
| 04 | The Rhythm | approved | 925 | 0 | 3 | passed §5a + §5b (verdict recovered from review-log; live reply dropped) |
| 05 | What She Stayed For | approved | 999 | 0 | 3 | passed §5a + §5b |
| 06 | The Automation's Lie | approved | 937 | 0 | 3 | passed §5a + §5b |
| 07 | The Thing in the Log | approved | 925 | 0 | 3 | passed §5a + §5b (ambiguity peak held) |
| 08 | The Long Watch | approved | 935 | 0 | 3 | passed §5a + §5b |
| 09 | First Light | approved | 942 | 0 | 3 | passed §5a + §5b (ch01 callbacks land) |
| 10 | The Beacon | approved | 924 | 0 | 3 | passed §5a + §5b (final ambiguity holds; recolourings land) |

### Status values

- `pending` — not yet dispatched
- `queued-for-writing` — writer has been (or is about to be) asked to write it
- `written` — writer saved the chunk; awaiting orchestrator
- `queued-for-review` — reviewer has been asked to review it
- `approved` — passed review; counts toward target (stamped with Spec-ver)
- `rejected` — failed review; will be re-queued for writing (see Notes)
- `needs-human` — failed review 3× (retry cap); paused for a human

### Run-status values (Summary line)

- `not started` / `in progress` — the chunk loop is running
- `assembling` — all chunks approved; builder is assembling the deliverable
- `evaluating` — evaluator is scoring the assembled whole (`spec.md` §9)
- `revising (eval round N)` — eval failed; implicated chunks are being reworked
- `complete (eval-passed)` — evaluator PASS; run finished
- `needs-human` — eval failed after 2 rounds (or a chunk hit its retry cap)
