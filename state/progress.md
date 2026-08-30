# Progress — coordination bus

**Owner: orchestrator only.** All other agents read this file; only the
orchestrator changes status. Seeded from `spec.md` §4 at the start of a run.

## Summary

- **Spec-Version:** 4
- **Target:** 10,000 words (plus or minus 10%)
- **Approved so far:** 10,030 words (10 of 10 re-approved at v4; within 9,000–11,000 tolerance) — run 02 targeted revision pass
- **Run status:** complete (eval-passed)
- **Eval rounds used:** 1 of 2
- **Latest eval:** Round 1 (run 02) PASS : overall 4.71 / 5 (Opus 5, Gemini 3.7 Flash), no dimension below 4. Arc 5, Ambiguity 5, Voice 5, Pacing 4, Prose 4, Coda 5, Themes 5. See `state/eval-report.md`.

Run 02 is a **revision pass**, not a from-scratch write: run-01 prose scored
4.1–4.4 across a four-model panel and is preserved. Each chunk is revised in
place against Spec-Version 4 (§4 reveal ledger, §7 relief-keeper canon, §5a
extended UK grep, §5b reveal/pacing/relief checks, §5c whole-work gates), then
re-run through §5a, re-reviewed at §5b, and re-stamped at v4. Light-scope chunks
get a surgical pass (change only what is named), not a rewrite.

### Run counters (orchestrator maintains during the run; dumped into the run log at completion)

- Mechanical-gate bounces by type: em/en-dash 0, length 1, prose-only 0, UK-spelling 0, second-person 0
- Editorial rejects (reviewer FAIL): 1
- Process friction: 0

The per-chunk `Retries` column already records total rewrites per chunk; these
counters break that total down by cause for the run log.

`Spec-ver` records the Spec-Version each chunk was approved under. On startup the
orchestrator compares it to the current Spec-Version; any `approved` chunk with a
lower value is stale and gets re-queued for a revision pass.

## Chunks

| # | Title | Status | Words | Retries | Spec-ver | Notes |
|---|-------|--------|-------|---------|----------|-------|
| 01 | The Road Back | approved | 1095 | 0 | 4 | v4 revision approved; §5a+§5b pass; the-way 4→1; reveal/relief/recolour continuity confirmed |
| 02 | The Keeper's Room | approved | 1063 | 0 | 4 | v4 revision approved; §5a+§5b pass; reveal-ownership verified line-by-line (seed only, ch03 discovery preserved); relief coverage affirmed |
| 03 | The Ledger | approved | 1037 | 1 | 4 | v4 approved on rewrite; §5a+§5b pass; relief-keeper canon fixed + reveal-ownership fixed (P15 no longer pre-empts ch06); 1 editorial reject |
| 04 | The Rhythm | approved | 1012 | 0 | 4 | v4 approved; §5a+§5b pass; owns answering-night (dramatised here), present-time anchored both ends, no forward-reach |
| 05 | What She Stayed For | approved | 1097 | 1 | 4 | v4 approved; §5a (after 1 length bounce) + §5b pass; doorway referenced-not-restaged (no ch02 overlap), pacing has present-time motion, vigil reframing owned |
| 06 | The Automation's Lie | approved | 1007 | 0 | 4 | v4 approved; §5a+§5b pass; toward→towards fixed; 17+3=20yr span explicit + canon-true; owns automation verdict (confined to sending side, ch07 open) |
| 07 | The Thing in the Log | approved | 924 | 0 | 4 | v4 approved; §5a+§5b pass; ambiguity peak fully intact (hedges preserved verbatim); the-way 2→1 |
| 08 | The Long Watch | approved | 929 | 0 | 4 | v4 approved; §5a+§5b pass; the-way 7→1 (densest chunk), hand-kept-watch prose intact |
| 09 | First Light | approved | 944 | 0 | 4 | v4 approved; §5a+§5b pass; the-way 3→1, "small competent" removed; ch01 callbacks + key/watch choice preserved |
| 10 | The Beacon | approved | 922 | 0 | 4 | v4 approved; §5a+§5b pass; toward→towards fixed; coda undisturbed (recolourings + double-hedged final line intact) |

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
- `whole-work checks` — running the §5c deterministic checks on the assembled whole (before eval)
- `evaluating` — evaluator is scoring the assembled whole (`spec.md` §9)
- `revising (eval round N)` — eval failed; implicated chunks are being reworked
- `complete (eval-passed)` — evaluator PASS; run finished
- `needs-human` — eval failed after 2 rounds (or a chunk hit its retry cap)
