# Progress — coordination bus

**Owner: orchestrator only.** All other agents read this file; only the
orchestrator changes status. Seeded from `spec.md` §4 at the start of a run.

## Summary

- **Spec-Version:** 2
- **Target:** 3,000 words (± 15%)
- **Approved so far:** 3139 words
- **Run status:** complete (de-dashed; output verified em-dash-free)

`Spec-ver` records the Spec-Version each chunk was approved under. On startup the
orchestrator compares it to the current Spec-Version; any `approved` chunk with a
lower value is stale and gets re-queued for a revision pass.

## Chunks

| # | Title | Status | Words | Retries | Spec-ver | Notes |
|---|-------|--------|-------|---------|----------|-------|
| 01 | The Road Back | approved | 1012 | 0 | 2 | de-dashed; complies with v2 (no em/en-dash, §7 canon) |
| 02 | The Keeper's Room | approved | 1087 | 1 | 2 | de-dashed; complies with v2 |
| 03 | First Light | approved | 1040 | 0 | 2 | de-dashed; complies with v2 |

### Status values

- `pending` — not yet dispatched
- `queued-for-writing` — writer has been (or is about to be) asked to write it
- `written` — writer saved the chunk; awaiting orchestrator
- `queued-for-review` — reviewer has been asked to review it
- `approved` — passed review; counts toward target
- `rejected` — failed review; will be re-queued for writing (see Notes)
- `needs-human` — failed review 3× (retry cap); paused for a human
