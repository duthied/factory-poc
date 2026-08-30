# Run index — metrics per run

Persistent, **one row per completed run** in each table below, newest at the
bottom. Never reset or archived (unlike `state/`), so you can watch every metric
change run over run. Full narrative detail for each run is in its
`YYYY-MM-DD-<slug>-runNN.md` file; the full flat metric row (all columns, for
sorting/charting) is in `runs/metrics.csv`.

The orchestrator appends a row to **both tables** and to `metrics.csv` as the
last step of every run (whether it finished `complete` or stopped at
`needs-human`). Read down any column to see that metric's trend.

## Quality trend (eval scores, 1-5 each)

| Run | Date | Spec-ver | Words | Eval | Overall | Arc | Ambig | Voice | Pacing | Prose | Coda | Themes |
|-----|------|----------|-------|------|---------|-----|-------|-------|--------|-------|------|--------|
| 01 | 2026-08-30 | 3 | 9709 | PASS | 4.4 | 4 | 5 | 4 | 4 | 4 | 5 | 5 |

## Process trend (effort & friction)

| Run | Date | Chunks (appr/plan) | Rewrites | Dash | Length | Prose-only | Spelling | 2nd-person | Ed. rejects | Eval rounds | Friction |
|-----|------|--------------------|----------|------|--------|------------|----------|------------|-------------|-------------|----------|
| 01 | 2026-08-30 | 10/10 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | chunk-04 reply dropped, ~13min stall, recovered from review-log |

Column notes: **Dash / Length / Prose-only / Spelling / 2nd-person** are
mechanical-gate bounce counts by type; **Ed. rejects** are editorial reviewer
FAILs; **Rewrites** is the sum of all per-chunk retries; **Friction** is a short
note (stalls, unreachable agents) or "none".
