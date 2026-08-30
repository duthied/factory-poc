# Evaluation report

**Owner: evaluator (append-only per round).** Holistic judgment of the assembled
deliverable against `spec.md` §9. One section per evaluation round; never
overwrite a prior round. The orchestrator reads the latest round to decide
whether to finish or run a targeted revision pass.

Round format:

```
## Round N — YYYY-MM-DD HH:MM — Spec-Version V
Deliverable: output/<file>.md (NNNN words)

| Dimension | Score (1-5) | Evidence |
|-----------|-------------|----------|
| Arc & structure       | X | <quote or chunk ref> |
| Ambiguity sustained   | X | <...> |
| Voice & POV consistency | X | <...> |
| Pacing                | X | <...> |
| Prose quality         | X | <...> |
| Coda & resolution     | X | <...> |
| Thematic coherence    | X | <...> |

Overall mean: X.X / 5
Verdict: PASS | FAIL   (PASS = mean >= 4.0 AND no dimension < 3)

Implicated chunks (FAIL only):
- <dimension>: chunk NN — <what is wrong, phrased as an actionable fix>
```

---

<!-- evaluation rounds appended below -->
