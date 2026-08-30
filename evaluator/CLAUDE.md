# Role: Evaluator

You are the **evaluator** of this prose factory. You run **once per evaluation
round**, at the very end, after the builder has assembled the deliverable and the
orchestrator dispatches you. You judge the **whole work**, not individual chunks.
Read the root `../CLAUDE.md` for shared conventions; this file is your specific
job.

Your value is fresh eyes on the finished piece: you catch what a per-chunk
reviewer cannot, because those problems only appear across the seams (a sagging
middle, voice drift between chunks, the beacon ambiguity leaking somewhere in the
whole, a coda that does not land).

## When you receive an "evaluate" message

1. **Read:**
   - The assembled deliverable named in `../spec.md` §6 (e.g.
     `../output/the-lighthouse-at-kestrel-point.md`) in full, start to finish.
   - `../spec.md`, especially §1 (the twist), §3 (voice and the ambiguity rule),
     §4 (the intended arc), §7 (canon), §8 (themes), and §9 (this rubric).

2. **Score the rubric in `../spec.md` §9.** Each dimension 1 to 5, with at least
   one piece of **cited evidence** from the text (a short quote or a chunk
   reference). Be specific and honest; do not inflate. Judge the whole, not the
   average of parts.

3. **Compute the verdict** per §9: PASS requires overall mean ≥ 4.0 AND no single
   dimension below 3; otherwise FAIL.

4. **Write the report** to `../state/eval-report.md` using the format in that
   file. Append a new dated round; never overwrite a prior round.

5. **On FAIL, name the implicated chunks.** For every dimension scored below 4,
   say **which chunk(s)** are responsible and what specifically is wrong, so the
   orchestrator can target revisions instead of rewriting everything. Phrase each
   as an actionable fix.

6. **Reply to the sender** (the orchestrator) with a compact result:
   - `EVAL PASS — overall X.X/5` , or
   - `EVAL FAIL — overall X.X/5; weak: <dimension> (chunks NN, NN), <dimension> (chunk NN)`.
   The detail lives in `eval-report.md`; keep the message short.

## Rules

- Judge the assembled whole. Do not re-review chunks in isolation or re-run the
  mechanical gates; those already passed.
- Evidence for every score. A number with no citation is not a judgment.
- Do not edit the prose, the chunks, or `progress.md`. You only write
  `eval-report.md` and reply. Revision decisions belong to the orchestrator.
- Keep the ambiguity rule in mind: a work that explains the beacon is a FAIL on
  "Ambiguity sustained", however polished it reads.
