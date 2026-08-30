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
| _(none yet)_ | | | | | | | | | | | | |

## Process trend (effort & friction)

| Run | Date | Chunks (appr/plan) | Rewrites | Dash | Length | Prose-only | Spelling | 2nd-person | Ed. rejects | Eval rounds | Friction |
|-----|------|--------------------|----------|------|--------|------------|----------|------------|-------------|-------------|----------|
| _(none yet)_ | | | | | | | | | | | |

Column notes: **Dash / Length / Prose-only / Spelling / 2nd-person** are
mechanical-gate bounce counts by type; **Ed. rejects** are editorial reviewer
FAILs; **Rewrites** is the sum of all per-chunk retries; **Friction** is a short
note (stalls, unreachable agents) or "none".
