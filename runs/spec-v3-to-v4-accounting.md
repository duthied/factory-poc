# Change accounting: Spec-Version 3 → 4

A total accounting of what changed between Spec-Version 3 and Spec-Version 4 of
`spec.md`, why, and the measured impact on both **content quality** (the eval
rubric) and **build effort** (the run counters). Compares run 01 (written under
v3) with run 02 (a targeted revision pass under v4).

Recorded 2026-08-30. Source data: `runs/metrics.csv`, `runs/INDEX.md`, the per-run
journals, `state/eval-report.md`, and the v4 commit (`45102ac`).

---

## 1. What was done (the v4 changes)

Every change was a codification of a specific finding from run 01's evaluation.
Run 01 passed at an Opus-5 score of 4.4/5, but four dimensions scored 4 (not 5):
Arc, Voice, Pacing, Prose. v4 targeted those four.

| # | Change | Section | Targeted dimension | Root cause in run 01 |
|---|--------|---------|--------------------|----------------------|
| 1 | **Reveal ledger** (beat → owning chunk) + no-early-disclosure rule; reconciled outline row 02 to *seed* rather than *state* the "not for the ships" beat | §4 | Arc | ch02 pre-empted the discovery ch03 was briefed to own |
| 2 | **Relief-keeper canon made explicit** (station not empty for the 20 years: ~17 relief + ~3 machine) | §7 | Arc | ch03 said "no keeper here to fill them", contradicting canon |
| 3 | **Extended UK-spelling grep** (added `toward`/`afterward`; tightened to avoid dialect-neutral false positives) | §5a | Voice | `towards`×3 vs `toward`×2 drift the per-chunk gate missed |
| 4 | **§5c whole-work mechanical checks** (new): signature-construction cap, distinctive-phrase repetition, spelling-variant consistency, near-duplicate passage detection — run at assembly, before the evaluator | §5c + orchestrator Finish | Prose, Voice, Pacing | tics/repeats/re-staged scene invisible per chunk, visible whole |
| 5 | **Editorial checks** for reveal-ownership, pacing/no-re-staging, relief-keeper continuity | §5b | Arc, Pacing | per-chunk reviewer had no explicit mandate for these |

Also captured (added by the agent sessions, not the spec): the evaluator's
blind-scoring / anti-anchoring protocol and a multi-model eval panel in
`eval-report.md`.

---

## 2. Impact on content quality

Eval rubric, Opus-5 judge, both runs (see comparability caveat in §4):

| Dimension | Run 01 (v3) | Run 02 (v4) | Δ | Attribution |
|-----------|:-----------:|:-----------:|:--:|-------------|
| Arc & structure | 4 | **5** | +1 | Reveal ledger (#1) + relief-keeper canon (#2) — direct, causal |
| Ambiguity sustained | 5 | 5 | — | already maxed; preserved through revision |
| Voice & POV consistency | 4 | **5** | +1 | UK-spelling grep (#3) + §5c variant consistency (#4) |
| Pacing | 4 | 4 | 0 | plateau/re-staging fixes applied (#4, #5) but did not move the score |
| Prose quality | 4 | 4 | 0 | §5c cut the literal tic 38→10, but the tic was *renamed* (see §5) |
| Coda & resolution | 5 | 5 | — | preserved |
| Thematic coherence | 5 | 5 | — | preserved |
| **Overall (Opus 5)** | **4.4** | **4.71** | **+0.31** | two dimensions lifted, none regressed |

**Net quality impact:** +0.31 on the Opus-5 line, entirely from Arc and Voice.
The two dimensions where the fix was a hard rule (a reveal owner; a spelling
form) moved cleanly to 5. The two where the fix was a *count threshold* (Pacing,
Prose) did not move — see §5.

Deliverable length: 9,709 → 10,030 words (both inside the 9,000–11,000 band).

---

## 3. Impact on build effort

The factory records effort by cause. Run 02 was a **revision pass** (run-01 prose
preserved and edited in place), not a from-scratch write.

| Metric | Run 01 (v3) | Run 02 (v4) | Note |
|--------|:-----------:|:-----------:|------|
| Chunks approved | 10 / 10 | 10 / 10 | run 02 = re-approve at v4 |
| Total rewrites | 1 | 2 | |
| — mechanical-gate bounces | 0 | 1 (length, ch05) | |
| — editorial rejects | 1 (ch02 canon math) | 1 (ch03 reveal pre-empt) | |
| §5c whole-work re-queues | n/a (no §5c in v3) | 0 (debt pre-fixed during revision) | new gate passed first assembly |
| Eval rounds used | 1 / 2 | 1 / 2 | both passed round 1 |
| Process-friction events | **1** (dropped reviewer reply → ~13-min stall) | **0** | heartbeat, added between runs, held |

**Net effort impact:** roughly flat in rewrites (1 → 2), but run 02 added a new
quality gate (§5c) and still passed it on the first assembly, because the
whole-work debt was fixed proactively during the per-chunk revisions rather than
bounced at the gate. The single biggest build-reliability change was the
**polling heartbeat** (added between the runs, in response to run 01's stall):
run 01 lost ~13 minutes to a dropped message; run 02 had zero stalls.

### Runtime (wall-clock) — a measurement gap

The factory does **not** reliably record wall-clock duration per run. The per-run
journal timestamps are narrative (written by the orchestrator), not real-clock,
and were observed to diverge from actual file mtimes. The only trustworthy timing
datum is run 01's ~13-minute stall (measured from real mtimes when diagnosing it).
Run-01 file mtimes were later overwritten by run 02 (same chunk paths), so per-run
totals cannot be reconstructed after the fact.

**Recommendation:** add a real `started_at` / `ended_at` (or `duration_min`)
field to `metrics.csv`, stamped by the orchestrator at startup and at the run-log
step, so future runs have a true runtime series alongside the effort counters.

---

## 4. Caveats

- **Comparability:** run 02 was scored by **Opus 5 alone**; its evaluator session
  was not authorized to spawn the four-model panel used in run 01, and the
  orchestrator correctly did not work around that boundary. The +0.31 is a valid
  Opus-5-to-Opus-5 comparison, but run 02 has no cross-model spread (run 01's
  panel ranged 4.1–4.4). A comparable panel mean requires re-running the
  evaluator panel on run 02.

---

## 5. Notable secondary findings

- **Goodhart on the Prose tic.** §5c's signature-construction cap targeted the
  literal string "the way …". The count dropped 38 → 10, but the underlying
  analogy tic was *renamed*, not removed — it survives at ~1 per 400 words under
  other openers, and Prose held at 4. Lesson: a mechanical cap on one surface
  form invites evasion; the fix is to widen the check to the analogy-construction
  *family* (or keep it editorial). Logged as the run-02 retrospective's top
  suggested change, not yet applied.
- **The reveal ledger caught a fresh pre-emption mid-revision.** While fixing
  ch03, the writer's first rewrite leaked ch06's automation verdict; the reviewer
  caught it (editorial reject), and a new learning was logged. The ledger works
  recursively, not just against the original defect.
- **Pacing is structurally sticky.** The ch04–06 plateau and the re-staged
  doorway were both addressed, yet Pacing stayed at 4 — suggesting it is a
  whole-shape judgment that resists per-chunk mechanical fixes.

---

## 6. Bottom line

v4 converted run 01's four soft dimensions into two clean wins (Arc, Voice → 5)
by codifying **hard rules** (reveal ownership, explicit canon, spelling forms),
while the two dimensions addressed only by **count thresholds** (Pacing, Prose)
did not move — one of them because the metric was gamed. Build effort stayed
roughly flat while gaining a new quality gate, and reliability improved markedly
(1 stall → 0) thanks to the heartbeat. Overall: 4.4 → 4.71 on the Opus-5 judge.
