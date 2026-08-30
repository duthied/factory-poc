# Progress — coordination bus

**Owner: orchestrator only.** All other agents read this file; only the
orchestrator changes status. Seeded from `spec.md` §4 at the start of a run.

## Summary

- **Spec-Version:** 3
- **Target:** 10,000 words (plus or minus 10%)
- **Approved so far:** 0 words
- **Run status:** not started (v3 science-fiction reconception; ready to begin)
- **Eval rounds used:** 0 of 2
- **Latest eval:** not yet run (see `state/eval-report.md`)

`Spec-ver` records the Spec-Version each chunk was approved under. On startup the
orchestrator compares it to the current Spec-Version; any `approved` chunk with a
lower value is stale and gets re-queued for a revision pass.

## Chunks

| # | Title | Status | Words | Retries | Spec-ver | Notes |
|---|-------|--------|-------|---------|----------|-------|
| 01 | The Road Back | queued-for-writing | — | 0 | — | seed faint wrongness in the lamp's rhythm |
| 02 | The Keeper's Room | pending | — | 0 | — | plant that the logs were never weather/shipping |
| 03 | The Ledger | pending | — | 0 | — | old logbooks; light's true work surfaces |
| 04 | The Rhythm | pending | — | 0 | — | predecessor teaches the cadence; the one rule |
| 05 | What She Stayed For | pending | — | 0 | — | Tomas refusal reframed as the vigil's cost |
| 06 | The Automation's Lie | pending | — | 0 | — | machine keeps the flash, not the true rhythm |
| 07 | The Thing in the Log | pending | — | 0 | — | ambiguous response; do not resolve |
| 08 | The Long Watch | pending | — | 0 | — | keeps one night watch by hand; the toll |
| 09 | First Light | pending | — | 0 | — | dawn; the choice about the key; ch01 callback |
| 10 | The Beacon | pending | — | 0 | — | coda; recolour ch01 images; leave it open |

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
