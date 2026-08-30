# Review log

**Owner: reviewer (append-only).** One entry per review. Never edit past
entries — append new ones. The orchestrator and humans read this to understand
why a chunk passed or failed.

Entry format:

```
## chunk-NN — attempt N — YYYY-MM-DD HH:MM
Verdict: PASS | FAIL
Checked against: spec.md §5 acceptance criteria
Findings:
- <what was right / what was wrong, per criterion>
Learnings appended: <yes/no — if yes, what was added to learnings.md>
```

---

<!-- entries appended below -->

## chunk-01 — attempt 1 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5 acceptance criteria
Findings:
- On-brief: covers outline row 01 fully — Maren's 20-year return, her establishment (61, arrived at 19, former resident), the coastal setting, and the lighthouse's automation (solar panel, aerial, grey housing, "the thing turning without hands"). Ends exactly as briefed, at the door ("She lifted her hand to the wood.").
- Length: 1015 words, within the 900–1,100 band.
- Voice/POV/tense: third-person limited on Maren, past tense throughout, warm/restrained/melancholy tone. UK spelling confirmed (colour, grey, harbour). No second person.
- Continuity: first chunk; nothing to contradict. Tomas correctly deferred to chunk 02.
- No contradictions with spec.
- Prose only — no headers, lists, or meta-commentary.
- Interiority shown, not stated — sensory and indirect (e.g. the fingers closing on the key without taking it out); no bald emotion-labelling.
Learnings appended: no (clean pass).

## chunk-02 — attempt 1 — 2026-08-30 00:00
Verdict: FAIL
Checked against: spec.md §5 acceptance criteria
Findings:
- On-brief: PASS in substance — interior of the keeper's room, memory braided with present, the reason she left (chose the light over Tomas), Tomas as the man she chose not to follow, and the duty-vs-forgone-life tension are all established.
- Length: PASS — 1067 words, within 900–1,100.
- Continuity: FAIL — timeline contradicts approved chunk-01. chunk-01 establishes she left ~20 years ago at age 41 and has lived inland the two decades since ("She had been forty-one the last time this road had carried her"; "had spent two decades in inland rooms"). chunk-02 instead has her tending the light continuously until automation: "She had stayed until they took the deciding out of her hands… left her, at fifty-nine, a keeper of nothing. And then she had gone — inland." Irreconcilable: 20 years away (last present at 41) vs. keeper until ~59 (≈2 years ago). Internally chunk-02 is consistent (Tomas at 38, choice recurring "twenty years", automation at 59), but that internal timeline is the wrong one — chunk-01 is approved and fixes the timeline.
- No contradictions with spec: FAIL — same issue also contradicts the spec brief/outline row 01 ("after 20 years") and §1 premise.
- Voice/POV/tense: PARTIAL — third-person limited on Maren, past tense, UK spelling all correct, BUT three uses of impersonal second person breach §3 "no second person": "It only holds what you carry in"; "the way you know a thing in the body before the mind consents to it"; "a thing you did not have to keep choosing." Recast to "one" or rephrase.
- Prose only: PASS.
- Shows rather than states interiority: PASS — restrained and largely dramatised.
Learnings appended: yes — (1) honour chunk-01's fixed timeline; (2) avoid impersonal second person per §3.

## chunk-02 — attempt 2 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5 acceptance criteria (re-review of the rewrite for attempt-1 FAIL)
Findings:
- Continuity (prior FAIL): RESOLVED. Timeline now consistent with chunk-01 — she kept the light three more years after Tomas, put in her notice "at forty-one" and "gone inland," with "the letter about the automation" reaching her "years later." Matches chunk-01 (left at 41, two decades inland, automation letter ~3 years ago).
- Second person (prior breach): RESOLVED. Zero you/your instances (grep-confirmed); offending lines recast to "what a person carries in" and "the way the body knows a thing."
- On-brief: PASS — keeper's-room interior, memory braided with present, reason she left (chose the light over Tomas), Tomas as the man not followed, duty-vs-forgone-life tension.
- Length: PASS — 1100 words, at the inclusive upper bound of 900–1,100.
- Voice/POV/tense: PASS — third-person limited on Maren, past tense, UK spelling.
- No contradictions with spec: PASS — "after 20 years" now holds.
- Prose only: PASS. Shows rather than states interiority: PASS.
Learnings appended: no (clean pass on re-review).

## chunk-03 — attempt 1 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5 acceptance criteria
Findings:
- On-brief: PASS — dawn; the small concrete choice (setting the key down in the scald mark and leaving it, relinquishing her claim) resolves her relationship to the place. Quiet, earned, not tidy ("It was not forgiveness"; "the question did not resolve"; "it did not make her whole, and she found she could live inside that").
- chunk-01 callback: PASS, lands strongly and multiply. The key is the central callback — chunk-01 ended with her hand closing around the unturned key at the door; chunk-03 resolves that gesture by setting it down. Reinforced by the verbatim "grey plate… flung wide beneath a sky the colour of wet slate," "Her hands on the wheel looked older," the scald-mark "pale comma," and the gate gap between two posts.
- Length: PASS — 1047 words, within 900–1,100.
- Voice/POV/tense: PASS — third-person limited on Maren, past tense, UK spelling; no second person (grep-confirmed zero you/your; uses "a body"/"a person" per the learnings).
- Continuity: PASS — timeline consistent (key carried "twenty years and more"; Tomas "at thirty-eight"); faithful reuse of his chair, the grey housing/automated cell, scald mark, gate posts. "carried, unturned, for twenty years and more" reads as the two-decade dormancy before yesterday's entry (chunk-02), i.e. retrospective — not a contradiction.
- No contradictions with spec: PASS — resolves the §1 premise.
- Prose only: PASS. Shows rather than states interiority: PASS — reflective close, no bald emotion-labelling.
Learnings appended: no (clean pass; the two prior learnings were correctly applied here).

## chunk-01 — attempt 2 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5 (re-review after de-dash revision; new criterion "No em-dashes anywhere")
Findings:
- No em-dashes: PASS — zero "—" and zero en-dashes "–" (grep-confirmed); no spaced-hyphen substitutes. Recast to commas/colons/full stops idiomatically (e.g. "not gradually but all at once"; "She had a key. They had let her keep a key"; L13 "letter from the authority three years ago. It said the light was automated now").
- Length: PASS — 1012 words.
- Voice/POV/tense/UK spelling: PASS — unchanged; no second person introduced.
- Continuity/on-brief/prose-only/shows-not-states: PASS — content unchanged from approved version.
Learnings appended: no.

## chunk-02 — attempt 3 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5 (re-review after de-dash revision)
Findings:
- No em-dashes: PASS — zero em/en-dashes (grep-confirmed); no spaced-hyphen substitutes. Recast cleanly (e.g. "the chair by the range, his chair, though…"; "When he did ask, plainly, on the last night the boat could wait, she had been standing…"; "let herself wonder, plainly, the way he had asked plainly,").
- Length: PASS — 1087 words.
- Voice/POV/tense/UK spelling: PASS — no second person; timeline still consistent (Tomas at 38, three more years, notice at 41, inland, letter years later).
- Continuity/on-brief/prose-only/shows-not-states: PASS.
Learnings appended: no.

## chunk-03 — attempt 2 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5 (re-review after de-dash revision)
Findings:
- No em-dashes: PASS — zero em/en-dashes (grep-confirmed); no spaced-hyphen substitutes. Recast cleanly (e.g. "coat pocket, the cold iron shape of it… for twenty years and more, and she looked"; "put down the thing she had been holding: not the man…"; "The olive trees, she thought, not with grief now").
- Length: PASS — 1040 words.
- Voice/POV/tense/UK spelling: PASS — no second person.
- Continuity/on-brief/callback/prose-only/shows-not-states: PASS — key-in-the-scald-mark choice and chunk-01 callbacks intact.
Learnings appended: no.
