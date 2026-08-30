# Review log

**Owner: reviewer (append-only).** One entry per review. Never edit past
entries, append new ones. The orchestrator and humans read this to understand
why a chunk passed or failed.

> Fresh log for the v3 run (Spec-Version 3, the science-fiction reconception).
> The v2 literary run's review history is preserved in
> `archive/v2-literary/review-log.md`.

Entry format:

```
## chunk-NN — attempt N — YYYY-MM-DD HH:MM
Verdict: PASS | FAIL
Checked against: spec.md §5b editorial criteria (mechanical gates §5a passed upstream)
Findings:
- <what was right / what was wrong, per criterion>
Learnings appended: <yes/no, and what if yes>
```

---

<!-- entries appended below -->

## chunk-01 — attempt 1 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5b editorial criteria (mechanical gates §5a passed upstream: 1098 words, zero em/en-dashes, prose-only, UK spelling, zero second-person hits)
Findings:
- On-brief / escalation curve: PASS — covers outline row 01 (drive to Kestrel Point after twenty years; establishes Maren, the coastal setting, the automation) and seeds exactly the one specified wrongness: the counting scene in P13, where her body anticipates the beam a half-beat before it arrives ("the way a foot finds a stair that is not there"), delivered by sensation and immediately rationalised by Maren herself. The P19 echo ("she did not count it this time, or tried not to") is a reprise of that same seed, not a second wrongness. Reads almost purely as quiet literary opening, as required. Ends exactly as briefed, at the door.
- Voice/tone/POV/tense: PASS — third-person limited on Maren, past tense, warm/restrained/sensory throughout.
- Continuity with §7 canon: PASS — ages and timeline exact (61 now, 41 twenty years ago, 19 on arrival, automated three years ago via letter); grey-plate/wet-slate horizon, kept key, scald mark, removed-gate/two-posts all present and consistent. No prior approved chunks in this v3 run to cross-check further.
- No contradictions with spec: PASS.
- Shows rather than states interiority: PASS.
- Ambiguity preserved: PASS — the seeded wrongness is legible either as an old woman's decades-old muscle memory misfiring, or as the true rhythm's absence per canon; both readings remain fully open. No naming/describing of a listener, no technobabble, no exposition dump.
Learnings appended: no (clean pass).

## chunk-02 — attempt 1 — 2026-08-30 00:00
Verdict: FAIL
Checked against: spec.md §5b editorial criteria (mechanical gates §5a passed upstream: 1070 words, zero em/en-dashes, prose-only, UK spelling, zero second-person hits)
Findings:
- Continuity with §7 canon: FAIL — P7 states she "had followed it faithfully for three and twenty years" (23 years). Canon fixes her arrival at 19 and departure at 41, a maximum possible keeping span of 22 years, and likely less since she "became the keeper" only after arriving (implying some interval before she held the post). 23 years exceeds even the absolute ceiling by one year regardless of how the apprenticeship period is read. This is the same category of unforced numeric contradiction flagged in the v2 run (see learnings). Recommend capping any restated span at "two and twenty years" / "twenty-two years" at the outside, or safer, using a vaguer phrase ("more than twenty years", "since she was little more than a girl") that cannot be falsified against future canon arithmetic.
- On-brief / plant: PASS — the nightly "logs were never weather" plant lands well ("a rhythm within the rhythm, a private arithmetic laid beneath the public one"), planted without exposition, matching escalation curve for row 02.
- Logbook scoping vs. chunk-03: PASS, not scope drift — she recalls the books exist but explicitly defers looking ("She would look. Not yet."), correctly reserving the physical discovery for chunk-03 "The Ledger".
- Voice/tone/POV/tense: PASS.
- Continuity otherwise (chunk-01, other canon facts): PASS — scald mark, chair, key, Tomas at 38 all consistent.
- No other spec contradictions: PASS (aside from the flagged age span).
- Shows rather than states interiority: PASS.
- Ambiguity preserved: PASS — no naming/describing the listener, no technobabble or exposition dump.
Learnings appended: yes — check every numeric age/duration a writer states against §7 canon arithmetic (19 to 41 is a hard 22-year ceiling for any "years of keeping" span) before it reaches review.

## chunk-02 — attempt 2 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5b editorial criteria (re-review of the rewrite for attempt-1 FAIL; mechanical gates §5a re-passed: 1071 words, zero em/en-dashes, prose-only, UK spelling, zero second-person hits)
Findings:
- Canon contradiction (prior FAIL): RESOLVED. P7 now reads "followed it faithfully for the whole of her keeping" — non-numeric, cannot conflict with §7 arithmetic. Confirmed the other stated ages remain within canon (26 for the scald-mark memory, 38 for Tomas's arrival, both inside the 19-41 window). No other text changed from attempt 1.
- On-brief / plant: PASS — unchanged from attempt 1, the "logs were never weather" plant still lands without exposition.
- Logbook scoping vs. chunk-03: PASS, unchanged, correctly deferred.
- Voice/tone/POV/tense: PASS, unchanged.
- Continuity with chunk-01 and §7 otherwise: PASS, unchanged.
- Ambiguity preserved: PASS, unchanged.
Learnings appended: no (the attempt-1 lesson already covers this case; re-review confirms the fix, no new lesson needed).

## chunk-03 — attempt 1 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5b editorial criteria (mechanical gates §5a passed upstream: 953 words, zero em/en-dashes, prose-only, UK spelling, zero second-person hits)
Findings:
- On-brief: PASS — opens the drawer left closed in chunk-02, finds the ledgers are not a real keeper's log: columns of timed marks against the lamp's turning ("Long. Short. Long, long."), an inherited notation with no written key, "handed, mouth to ear, keeper to keeper." First real sense the light's true work was not for ships ("It was not a keeper's log. It had never been a keeper's log, not really"). Escalation sits correctly in the middle of the curve: the truth surfaces through the object itself, never named or explained ("the light had its own patience and that hers was to match it").
- §7 canon continuity re: relief keepers (flagged for scrutiny): PASS, on close reading. The successor's hand "picking up the same discipline for a handful of months" then thinning to nothing, followed by two further blank books attributed to "no keeper here to fill them, only a grey box," could misread as claiming no human was ever stationed there again before automation, which would contradict "one or more relief keepers held the station" in §7. But "keeper" throughout this piece is used in the vigil-holding sense (distinct from ordinary staffing), and the passage is specifically about who continued the *notation*, not about physical staffing generally: relief keepers could hold the station on ordinary duty while never being taught, or never sustaining, the secret discipline. This reading is directly supported by §7's own line that the watch "has gone unanswered for the twenty years since she left" (not just the three years since automation) — the blank ledgers dramatise exactly that twenty-year lapse. No over-specification found; if anything this is a strong, canon-faithful piece of physical evidence for a fact the spec already states. Minor suggestion for the writer (not a fail): a single clarifying word (e.g. "no one left to keep the discipline" rather than bare "no keeper") would close off the less charitable reading entirely, but it is not required.
- Voice/tone/POV/tense: PASS — third-person limited, past tense, restrained.
- Shows rather than states interiority: PASS, with a minor note — "What frightened her now..." names an emotion directly, but it is immediately grounded in specific, concrete elaboration (the discontinuity of hands, the blank final page) rather than left as a bald label, which keeps it within the spirit of the criterion. Not a fail.
- No contradictions with spec: PASS.
- Ambiguity preserved: PASS — never confirms or denies the non-human, never names or describes a listener; the closing line ("deaf... to whatever the letter had only ever been a way of writing down") holds both readings open without resolving either.
Learnings appended: no (clean pass; flagged canon question resolved on inspection, no rule needed beyond existing §7 text).

## chunk-04 — attempt 1 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5b editorial criteria (mechanical gates §5a passed upstream: 925 words, zero em/en-dashes, prose-only, UK spelling, zero second-person hits; only numeric reference is "the twenty years after it", canon-consistent, no falsifiable span against the 19-41 keeping window)
Findings:
- On-brief: PASS — predecessor teaching the notation, the single rule ("Never break it"), the early "kept time back" night, and the vigil explicitly framed as oral inheritance ("handing her something that had been handed to him in exactly this manner, at exactly this table") are all present.
- Escalation / ambiguity on the pivotal beat: PASS, and well handled. The P9 "kept time back" moment is hedged throughout ("Nothing so clean as a sound", "she could never afterwards say which") and P11 keeps both readings alive to the last line ("it had been tiredness... or nothing at all" against "something on the other side of it was capable of noticing when it was kept"). Never adjudicated as real.
- Voice/tone/POV/tense: PASS.
- Shows rather than states interiority: PASS — sensation and behaviour carry it throughout, no bald emotion-labelling.
- §7 canon continuity: PASS — oral transmission keeper to keeper and the single rule match exactly; no numeric contradiction.
- No contradictions with spec: PASS.
- Ambiguity preserved: PASS — no naming/describing a listener, no sound or sighting confirmed as real, no technobabble or exposition dump.
Learnings appended: no (clean pass).

## chunk-05 — attempt 1 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5b editorial criteria (mechanical gates §5a passed upstream: 999 words, zero em/en-dashes, prose-only, UK spelling, zero second-person hits; only numeric reference is "in twenty years" (P7), canon-consistent with time since leaving/refusal)
Findings:
- On-brief / reframe: PASS — "the reason she stayed was smaller and stranger than duty" reframes the refusal exactly as briefed, culminating in "She had refused a life she wanted, for a possibility she could not prove", matching the outline's "a yes to something vast and unprovable". P9's ledger of stakes ("if she was wrong... but if she was right...") makes the human hinge meet the beacon scale directly, as required.
- Belief stays unconfirmed: PASS, rigorously hedged throughout ("without proof and without the hope of proof", "She had spent the rest of her life not deciding what that had been", "whatever had been on the other end, if anything had"). Never tips into confirmation.
- ch04 callback: PASS — the "kept time back" night is explicitly recalled (P7) as unresolved evidence consistent with how chunk-04 left it, and stays unadjudicated here too.
- Shows rather than states interiority (flagged for scrutiny, re: in-advance grief): PASS, with a minor note. "She had grieved for it in advance" names the emotion directly, but is immediately particularised by a specific comparison ("mourned a life she had never lived as thoroughly as some women mourn one they have lost") and concrete ritual detail ("alone, at the same table, between one turn of the beam and the next"), which keeps it within the spirit of the criterion. Same pattern as the chunk-03 "frightened her" note, passed on the same reasoning. Not a fail.
- Voice/tone/POV/tense: PASS.
- §7 canon continuity: PASS — Tomas, the olive trees/white house allusion, and the timeline all consistent; no numeric contradiction.
- No contradictions with spec: PASS.
- Ambiguity preserved: PASS — no naming/describing the listener, no technobabble or exposition dump.
Learnings appended: no (clean pass).

## chunk-05 — attempt 2 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5b editorial criteria, Spec-Version 4 revision pass (run 02), fixing the run-01 near-verbatim doorway re-staging and the ch04-06 pacing sag (mechanical gates §5a re-passed: 1097 words, zero em/en-dashes, prose-only, UK spelling, "towards"/"afterwards" consistent, "the way" construction at 1 occurrence at P3; zero second-person hits)
Findings:
- No re-staging (focus check 1): PASS, confirmed. P5 explicitly declines to replay the doorway: "The parting itself she no longer let herself replay in full, only the shape of it now, worn smooth by twenty years of handling," then compresses it into indirect summary. Checked for verbatim/near-identical overlap with ch02's doorway scene (searched for "Come with me," "his bag already packed," "the width of the little room," "someone else will keep the light") — none recur; the relief-keeper/ship-safety point is present but reworded ("A relief keeper would be sent and would learn the public turning inside a month. No ship on that coast would ever sail one degree less safe for her absence" vs. ch02's differently-worded original), a reference rather than a re-dramatisation. Ch04's answering-night is likewise only briefly alluded to ("She had felt it once, early in her keeping, in a way she had never afterwards managed to explain away entirely") with none of its specific sensory detail repeated, not retold.
- Pacing (focus check 2): PASS. Unlike a second static table-bound unit, ch05 gives Maren physical motion distinct from ch04: she rises and moves to the window (P3) and the chunk closes on her turning back into the room from the window (P13), bookending the memory with present-time frame and movement rather than sitting through it in place.
- Reveal ownership (focus check 3): PASS on its own beat — P7, P9, and P13 make the vigil-as-real-reason-for-refusal explicitly and centrally ch05's own ("not a no to Tomas so much as a yes to whatever it was she had once felt listening back"), matching outline row 05 exactly. Checked for ch06 reach: P9's "if she left... would go on being sent for a while... and would then, gradually, thin from habit into nothing" is examined closely — it stays entirely within a hypothetical, conditional register ("If she left, and if she was wrong... But if she left, and if she was right...") describing Maren's twenty-years-ago reasoning about a future that did not, in the story, come to pass this way, never naming "automation" or "the machine" or asserting anything about the *actual current* light. This is foreshadowing/dramatic irony, not the explicit, present-tense confirmation of automation's failure that is ch06's beat to deliver; it does not pre-empt ch06 the way the original chunk-03 P15 did.
- On-brief row 05: PASS — the refusal reframed exactly as briefed: "smaller and stranger than duty," "a yes to something vast and unprovable" realised almost verbatim in P13.
- Voice/tone/POV/tense: PASS.
- §7 canon continuity, incl. relief-keeper fact: PASS — "in twenty years" (P7, P9) consistent; no claim that the station sat untended, and P9's hypothetical about the listening "thinning into nothing" describes the practice, not physical staffing.
- Shows rather than states interiority: PASS, with the same minor, non-failing note as the original approval — "grieve for in advance" (P11) is immediately grounded in concrete elaboration ("mourned a life she had never lived... alone, at that same table, between one turn of the beam and the next").
- Ambiguity preserved: PASS — "whatever had been on the other end, if anything had" (P9) and the unresolved feeling in P7 never confirm the listener; no naming, describing, or technobabble anywhere.
Learnings appended: no (clean pass; both run-01 defects genuinely fixed).

## chunk-06 — attempt 1 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5b editorial criteria (mechanical gates §5a passed upstream: 937 words, zero em/en-dashes, prose-only, UK spelling, zero second-person hits; numeric references "Twenty years" x2 and "three years" both canon-consistent, and the "twenty years" claim is explicitly framed as "her own private and unprovable reckoning", not narrated fact)
Findings:
- On-brief: PASS — she examines the gutted mechanism and understands the machine "could only hold the note" where the true rhythm "breathed", matching the outline's "kept the surface, the machine lost the substance". Ties directly into the chunk-03 relief-keeper thread ("Her relief had come within the month... had kept the surface of it faithfully enough for a while... a stranger's hand thinning across the pages"), consistent with that chunk's ledger depiction.
- ch01 callback / consistency: PASS, checked closely. The half-beat wrongness is reinterpreted with narrative confidence ("It was not her body that had lost the beat. The beat itself had been wrong"), but this is appropriate: the mechanical fact being asserted (automation differs from the true rhythm) is already established §7 canon, not the part meant to stay ambiguous. The chunk correctly reserves its hedging for the part that must stay open, whether anything was listening at all ("by her own private and unprovable reckoning", "if a listener there had ever truly been"). Consistent with how chunk-01 seeded the wrongness.
- Ambiguity preserved (critical criterion): PASS. Never confirms the listener is real; the closing line does the load-bearing work explicitly ("did not know, could never know, whether she was grieving a fact or a story she had told herself so long it had grown teeth of its own"). No technobabble: the machinery is described sensorially/functionally ("a slim black unit bolted where the old clockwork drive had once sat", "a cable ran... into the lamp's turning gear"), never as sci-fi exposition.
- Voice/tone/POV/tense: PASS.
- Shows rather than states interiority: PASS — carried through physical action and the held-note musical metaphor; closing line is a genuine ambiguous meditation, not a bald emotion label.
- §7 canon continuity: PASS — automation "three years past now", "Twenty years" since leaving, relief-keeper chain from chunk-03, all consistent.
- No contradictions with spec: PASS.
Learnings appended: no (clean pass).

## chunk-06 — attempt 2 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5b editorial criteria, Spec-Version 4 revision pass (run 02), fixing the run-01 relief-keeper span gap-jump (mechanical gates §5a re-passed: 1007 words, zero em/en-dashes, prose-only, UK spelling — "toward" now "towards", "backwards" consistent, "the way" construction at 1 occurrence at P7; zero second-person hits)
Findings:
- Relief-keeper span (focus check 1): PASS, and the run-01 gap-jump is genuinely fixed. Revised P11 now states explicitly: "the station itself had not sat empty for the years that followed. One relief keeper after another had held it for the whole of the seventeen years after that, the light minded, the ships as safe as they had ever been, the ordinary record kept complete." The first relief keeper is shown attempting the true discipline "for a handful of uncertain months before it thinned and gave out," after which "none of them, so far as her own reading could tell, had ever taken up the other discipline again" — i.e. the public surface was kept faithfully throughout, only the vigil itself lapsed. The automation is placed at "three years past now," and 17 (relief) + 3 (automation) = the canon-correct twenty years. Nothing states or implies the station sat empty or unmanned across the whole span; the "had not sat empty" clause is a direct, affirmative correction of that misreading.
- Reveal ownership (focus check 2): PASS, and this is correctly ch06's own beat to deliver. P7 and P9 make the explicit verdict ("A machine could not hold that relation. A machine could only hold the note"; "It was not her body that had lost the beat. The beat itself had been wrong") and P11 explicitly states the twenty years unanswered. Checked for reach into ch07: P7's and P11's descriptions ("there was no longer any breath in the sending for a listener... to recognise as breath"; "had received back... only this: a wink, mechanical, exact, and utterly, utterly silent") are both about the failure of the *outgoing* signal (the sending side, ch06's own territory), not a claim about whether any response has been detected or is absent in the record, on the horizon, or in the sea, which stays reserved, unaddressed, and open for ch07 to explore. The listener's existence itself stays hedged throughout ("if a listener there had ever truly been," "her own private and unprovable reckoning").
- On-brief row 06: PASS — matches the outline exactly: she examines the new machinery, understands it keeps the flash pattern but not the true rhythm, and the listening has gone unanswered for twenty years; her replacement (the relief keepers) kept the surface, the machine finished losing the substance.
- Voice/tone/POV/tense: PASS.
- Shows rather than states interiority: PASS — the closing line ("did not know, could never know, whether she was grieving a fact or a story she had told herself so long it had grown teeth of its own") remains a genuine ambiguous meditation, not a bald label.
- Ambiguity preserved: PASS — never confirms the listener is real; no technobabble, the machinery described sensorially/functionally throughout ("a slim black unit bolted where the old clockwork drive had once sat," "a cable ran... into the lamp's turning gear").
- No contradictions with spec: PASS.
Learnings appended: no (clean pass; the run-01 relief-keeper gap-jump is genuinely fixed).

## chunk-07 — attempt 1 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5b editorial criteria, with ambiguity as the make-or-break test (mechanical gates §5a passed upstream: 925 words, zero em/en-dashes, prose-only, UK spelling, zero second-person hits, zero numeric age/duration references)
Findings:
- On-brief: PASS — the automated log's timing clusters resembling her notation ("Long. Short. Long, long.") and the sea's "held quality" are both present as the outline's "something in the automated record, or on the horizon, or in the sea's behaviour" that reads as a response or its absence. Whether it is real or pattern-seeking by a grieving keeper is explicitly posed and left open.
- Ambiguity preserved (critical): PASS, verified line by line. Observation 1 (timing clusters) is forcefully self-undercut in her own voice: "a sequence of tiny numbers could be arranged to resemble almost anything a person already carried in her head looking for it... Of course she had found it." Observation 2 (the sea) is hedged at every clause ("seemed to slacken", "as if... were listening rather than simply moving", "might have been a minute or might have been the length of time it takes a tired woman... to stop trusting her own eyes") and then explicitly dissolved ("the sea was only the sea again, doing what the sea did"). No third confirming fact was introduced; the two hedged observations are weighed against each other and found insufficient even together ("neither one enough alone, both together not quite enough either"). The close states that irresolution is structural and permanent ("There was no third fact waiting to arrive that would settle it... The not knowing was... the inheritance itself") without smuggling in an answer under cover of theme. No line anywhere confirms or denies the non-human; the listener is never named, described, or embodied.
- No technobabble: PASS — the automated log is rendered in flat, mundane manual language ("fell well within tolerance and required no action"), letting the skeptical reading speak in its own voice rather than only Maren's.
- Voice/tone/POV/tense: PASS.
- Shows rather than states interiority: PASS — strongest execution so far, carried entirely through reasoning and physical action with no bald emotion-labelling.
- §7 canon continuity: PASS — predecessor/oral-lineage reference consistent with chunk-04; no numeric claims to conflict with canon.
- No contradictions with spec: PASS.
Learnings appended: no (clean pass).

## chunk-07 — attempt 2 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5b editorial criteria, Spec-Version 4 revision pass (run 02), light surgical edit (§5a re-passed: 924 words, zero em/en-dashes, prose-only, UK spelling, "afterwards" consistent, "the way" construction thinned from 2 to 1 occurrence at P5; zero second-person hits)
Findings:
- Ambiguity peak preserved (make-or-break, focus check): PASS, confirmed intact and unchanged. Verified every load-bearing hedge from the prior approval is present verbatim: "a sequence of tiny numbers could be arranged to resemble almost anything a person already carried in her head looking for it... Of course she had found it" (P5); "seemed to slacken," "as if... were listening rather than simply moving," "might have been a minute or might have been the length of time it takes a tired woman... to stop trusting her own eyes" (P9); "the sea was only the sea again, doing what the sea did" (P9); "There was no third fact waiting to arrive that would settle it... The not knowing was... the inheritance itself" (P13). No line confirms or denies the non-human; the listener is never named, described, or embodied. The one-word-level "the way" thinning did not touch any of this.
- Reveal ownership: PASS — does not re-deliver ch06's automation verdict (no restatement of the flash-vs-rhythm claim); P15's closing ("find out whether a true watch, kept by hand for one full night the old way, changed anything at all... She went inside to find the old pen") announces her intent and transitions toward ch08 without dramatising the watch itself, its toll, or any of its content, so ch08's beat is not disclosed.
- On-brief row 07: PASS, unchanged — the timing clusters and the sea's held quality both read as a possible response or its absence, explicitly left unresolved.
- Voice/tone/POV/tense: PASS.
- §7 canon continuity: PASS.
- Shows rather than states interiority: PASS.
- No contradictions with spec: PASS.
Learnings appended: no (clean pass; surgical edit disturbed nothing).

## chunk-08 — attempt 1 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5b editorial criteria (mechanical gates §5a passed upstream: 935 words, zero em/en-dashes, prose-only, UK spelling, zero second-person hits; numeric references 61, 41, 26, 38, 41 all match established canon exactly, current age and prior memory-flashback ages)
Findings:
- On-brief: PASS — the watch is kept entirely by hand, re-establishing the rhythm through marking. P9 delivers the outline's "gathering her whole life into a single night" almost literally: Tomas, the predecessor, and her three younger selves (26, 38, 41) all converge at the same table "until it was difficult to say which of them was holding the pen."
- No new ambiguity beat introduced (key check): PASS, confirmed deliberate and explicit. She actively declines to look for a response: "She did not look for anything out past the beam... because looking had never been the discipline; the marking was the discipline, and whatever received it or did not receive it was never hers to confirm." Chunk-07's peak stands undisturbed; the chunk's power is entirely bodily and memorial, not evidentiary.
- Shows rather than states interiority (toll via the body): PASS, cleanest execution in the run so far. Cold rising foot to knee, "her back ached in the particular way that sixty-one years ache rather than... forty-one", eyes that "burned and watered and swam the beam into two beams and then one again." No bald emotion-labelling found anywhere.
- Voice/tone/POV/tense: PASS.
- §7 canon continuity: PASS — all five numeric age references consistent with established canon; oral-lineage "unbroken line of tired bodies" consistent with chunk-04.
- No contradictions with spec: PASS.
- Ambiguity preserved: PASS — no listener named/described, no technobabble, no new confirming or denying beat.
Learnings appended: no (clean pass).

## chunk-08 — attempt 2 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5b editorial criteria, Spec-Version 4 revision pass (run 02), the heaviest single §5c thinning in the run (mechanical gates §5a re-passed: 929 words, zero em/en-dashes, prose-only, UK spelling, no variant drift, "the way" construction thinned from 7 to 1 occurrence at P11; zero second-person hits)
Findings:
- Prose quality / show-don't-tell (focus check): PASS, the thinning did not flatten the prose. All the load-bearing sensory passages from the prior approval survive verbatim: "her back ached in the particular way that sixty-one years ache rather than forty-one" and "burned and watered and swam the beam into two beams and then one again" (P7); the whole-life convergence closing "until it was difficult to say which of them was holding the pen" (P9); the discipline-not-looking passage (P11). Where former "the way ..." constructions were removed, they were replaced with equally sensory comparative phrasing rather than flat summary: "as a hand that has not played an instrument in years still finds the correct string before the mind has quite caught up" (P5), "much as weather rises between fixed points on a chart" (P9), "matched by a hand that marked what it heard and held what it marked until the marking was done" (P3). The one remaining instance ("the way a person swimming a long distance stops fighting the water and is merely, for a while, carried," P11) is itself vivid and load-bearing, correctly kept rather than cut.
- On-brief row 08: PASS, unchanged — the watch kept entirely by hand, the toll on the body, and "gathering her whole life into a single night" (Tomas, the predecessor, and her three younger selves at 26, 38, 41) all land as before.
- Voice/tone/POV/tense: PASS.
- §7 canon continuity: PASS — all numeric age references (61, 41, 26, 38, 41) still consistent.
- Reveal ownership: PASS — checked P13's closing ("would be very nearly the last mark she would ever make in that book") for reach into ch09: it foreshadows without disclosing the specific key/watch choice ch09 owns, the same kind of forward hint already accepted in earlier chunk endings. P9's backward callbacks to Tomas, the predecessor, and her younger selves are compressed summary, not verbatim re-staging of any prior chunk's dramatised scene, and restate no ledger-owned beat (no automation verdict, no explicit vigil-as-refusal-reason framing beyond what ch05 already established).
- Ambiguity preserved: PASS — no listener named/described, no technobabble, no new confirming or denying beat; the deliberate non-looking passage stands undisturbed.
Learnings appended: no (clean pass; the heaviest §5c thinning in the run preserved prose quality).

## chunk-09 — attempt 1 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5b editorial criteria (mechanical gates §5a passed upstream: 942 words, zero em/en-dashes, prose-only, UK spelling, zero second-person hits; numeric references 26 and "twenty years" both match canon, and "turned only the evening before" correctly matches chunk-02's opening scene, no continuity break)
Findings:
- On-brief: PASS — automated lamp cuts at first light exactly as briefed. Both concrete choices flagged for review are present and deliberate: the filled logbook left open on the sill in plain sight rather than hidden, and the key left "standing in the lock, neither turned nor taken." Not tidy: the text explicitly names and rejects the tidy alternative ("Locking it would seal the place the way a grave is sealed, tidy, final") before choosing the irresolute gesture.
- Chunk-01 callback audit (all three checked, none token): PASS. The grey-plate/wet-slate horizon recurs in P1 with new weight. The door from chunk-01's closing line is explicitly named as the same door ("the one she had stood at with her hand raised, not yet knowing what waited on the other side of it"), the strongest of the three, closing an emotional loop opened at the very start of the book. The two bare gate posts recur in P13. All three are genuinely resonant and recontextualised, not repeated verbatim for its own sake.
- Human climax without beacon resolution: PASS — her relationship to the place resolves decisively (disclosure over concealment, ambivalence over finality) while the beacon question stays explicitly open: the close reads "no answer she could carry away and no proof that there had ever been a question worth asking... a door left open on the smallest chance that dark was not the last word either." Both readings remain available.
- Ambiguity preserved: PASS — nothing confirms or denies the listener, listener never named/described, no technobabble.
- Voice/tone/POV/tense: PASS.
- Shows rather than states interiority: PASS — no bald emotion-labelling found.
- §7 canon continuity: PASS — kept key, scald mark, horizon, gate posts all consistent; numeric references match canon.
- No contradictions with spec: PASS.
Learnings appended: no (clean pass).

## chunk-09 — attempt 2 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5b editorial criteria, Spec-Version 4 revision pass (run 02), two §5c fixes only (mechanical gates §5a re-passed: 944 words, zero em/en-dashes, prose-only, UK spelling, no variant drift, "the way" construction thinned from 3 to 1 occurrence at P11, "small competent" phrase removed; zero second-person hits)
Findings:
- Coda/callback preservation (focus check): PASS, all three ch01 callbacks confirmed intact verbatim: the grey-plate/wet-slate horizon (P1), the door named as the same one from ch01's closing line ("the one she had stood at with her hand raised, not yet knowing what waited on the other side of it," P11), and the two bare gate posts (P13). The retained "the way" instance ("Locking it would seal the place the way a grave is sealed, tidy, final," P11) is itself part of the key/watch choice and correctly kept, not cut.
- "Small competent" replacement: PASS, does not weaken the machine's characterisation. The phrase is gone; in its place, "obedient to a schedule that needed no one's hand on it" (P3) and "The machine could end the watch whenever it judged fit. It had never once been able to keep it" (P3) still deliver the machine's limited, mechanical nature and the contrast with Maren's vigil, arguably more pointedly than the removed phrase.
- On-brief row 09: PASS, unchanged — the lamp cuts at dawn, both concrete choices (book left open on the sill, key left standing in the lock) are present and deliberate, and the tidy alternative (locking it) is explicitly named and rejected.
- Reveal ownership: PASS — checked P13's closing against ch10's owned beat (the consequence, and "for the ships" reframed as the lie): the sea's silence stays explicitly unresolved ("no answer she could carry away and no proof that there had ever been a question worth asking... a door left open on the smallest chance that dark was not the last word either") without stating any consequence or touching the "for the ships" framing, both reserved for ch10.
- Voice/tone/POV/tense: PASS.
- §7 canon continuity: PASS — kept key, scald mark (26), horizon, gate posts, "twenty years," and "turned only the evening before" (matching chunk-02) all consistent.
- Shows rather than states interiority: PASS — no bald emotion-labelling.
- Ambiguity preserved: PASS — listener never named/described/confirmed.
Learnings appended: no (clean pass; both §5c fixes disturbed nothing substantive).

## chunk-10 — attempt 1 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5b editorial criteria, with the final-line ambiguity mandate as the make-or-break test (mechanical gates §5a passed upstream: 924 words, zero em/en-dashes, prose-only, UK spelling, zero second-person hits; numeric references twenty years, 26, 41 all match canon)
Findings:
- On-brief: PASS — unspectacular by design ("the flat held her, and the fridge hummed its small competent hum"); the public account "for the ships, and for no one" is quoted verbatim and framed as true-but-incomplete ("a thing could be entirely true and still not be the whole of what needed saying"), matching canon's own framing.
- Recolouring audit (all three checked): PASS, genuine transformation, not repetition. Horizon split into the ordinary visible one and "the other one now... past the reach of any beam a lamp could throw, the one she had never seen and never would." Key recoloured entirely as absence ("her hand went to the pocket... before she remembered... that it was not there"), closing on "whether that emptiness was loss or the first honest thing she had done in a very long time." Scald mark recoloured via the comma/full-stop metaphor ("A comma was not a full stop... the sentence... unfinished rather than ended").
- Ambiguity to the last line (critical): PASS, verified closely. The clause "a light... that had never lied to about anything except the one thing that mattered most" could misread as confirming a lie about the listener, but on inspection it refers to the established §7 canon fact that the secret rhythm-practice was real and omitted from the public account, not to the listener's existence, which stays separately open. The actual final clause, "no one, so far as she would ever be permitted to know, to receive it," is grammatically hedged by the epistemic clause: it asserts the limit of her knowledge, not the fact of no reception. Both readings survive intact to the final word. The listener is never named or described anywhere in the coda; no technobabble.
- Voice/tone/POV/tense: PASS.
- Shows rather than states interiority: PASS.
- §7 canon continuity: PASS — all numeric references match canon exactly.
- No contradictions with spec: PASS.
Learnings appended: no (clean pass; final chunk of the ten-chunk outline).

## chunk-01 — attempt 2 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5b editorial criteria, Spec-Version 4 revision pass (run 02), following the run-01 §5c signature-construction-cap fix (mechanical gates §5a re-passed: 1095 words, zero em/en-dashes, prose-only, UK spelling, no variant drift, "the way" construction thinned to 1 occurrence at P13; zero second-person hits to adjudicate)
Findings:
- On-brief / escalation curve: PASS — the thinning did not touch content, only the P13 simile phrasing. Still covers outline row 01 exactly (drive to Kestrel Point after twenty years, Maren, the coastal setting, the automation) and seeds exactly the one specified wrongness: the counting scene in P13, where her body registers the beam's arrival a half-beat off ("the way a foot finds a stair that is not there"), immediately rationalised by Maren herself ("a machine kept better time than any hand ever had"). The P19 echo ("she did not count it this time, or tried not to") remains a reprise of that same seed, not a second wrongness. Reads almost purely as quiet literary opening, as required. Ends exactly as briefed, at the door.
- Signature-construction cap (§5c, verified directly): confirmed exactly 1 occurrence of the "the way ..." construction in the chunk (`grep -inE 'the way (a|the|an|she|he|it|one|his|her|they)?'`), matching the orchestrator's report and resolving the run-01 over-cap defect for this chunk.
- Voice/tone/POV/tense: PASS — third-person limited on Maren, past tense, warm/restrained/sensory throughout, unchanged from the prior approval.
- Continuity with §7 canon: PASS — ages and timeline exact (61 now, 41 twenty years ago, 19 on arrival, automated three years ago via letter). Relief-keeper fact specifically checked: P9's "It looked cared for, and that was the wrong word... because there was no one there to care" and P15's automation/letter details read as present-tense observation of the current, post-automation state, not a retrospective claim that the station sat untended across the full twenty years; nothing in the chunk states or implies the station was unmanned before automation. Grey-plate/wet-slate horizon, kept key, scald mark, removed-gate/two-posts all present and consistent.
- Reveal ownership (§4 ledger): PASS — discloses only the ledger-owned beat for chunk 01 (faint lamp-rhythm wrongness, seed only, unexplained). No mention of the private notation (ch02), the ledgers/not-a-keeper's-log discovery (ch03), the oral inheritance or the one rule (ch04), the vigil as the reason for refusing Tomas (ch05), the automation's failure to hold the true rhythm (ch06 — P15 only observes that automation exists and keeps its own record, never claims it fails to reproduce anything), a possible response or its absence (ch07), the hand-kept watch (ch08), the key/watch choice (ch09), or the coda's consequence (ch10).
- Pacing / no re-staging: PASS — single chunk, nothing repeated within it.
- No contradictions with spec: PASS.
- Shows rather than states interiority: PASS.
- Ambiguity preserved: PASS — the seeded wrongness is legible either as an old woman's decades-old muscle memory misfiring, or as the true rhythm's absence per canon; both readings remain fully open. No naming/describing of a listener, no technobabble, no exposition dump.
Learnings appended: no (clean pass; revision confirms the §5c fix did not disturb any §5b criterion).

## chunk-02 — attempt 3 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5b editorial criteria, Spec-Version 4 revision pass (run 02), following the run-01 §5c signature-construction-cap fix (mechanical gates §5a re-passed: 1063 words, zero em/en-dashes, prose-only, UK spelling, "towards" x2 internally consistent, "the way" construction thinned to 1 occurrence at P7; zero second-person hits to adjudicate)
Findings:
- Reveal ownership (§4 ledger, the make-or-break check): PASS, verified line by line. P7 seeds only the ch02-owned beat: the private notation Maren followed "without ever fully understanding what it was she was recording," hinted via "marks... bore so little resemblance to the columns the weather book asked for: a rhythm within the rhythm, a private arithmetic laid beneath the public one." This text is unchanged verbatim from the previously-approved attempt 2 (already adjudicated clean on this exact point). No line states or has Maren realise that the records are "not a keeper's log," that they were "not for the ships," or that the light's true work was other than warning ships; that explicit surfacing stays reserved for ch03 ("She would look. Not yet.", P15). The disclosure remains at hint/unexamined-habit level throughout.
- On-brief: PASS — covers outline row 02: inside the cottage, memory of Tomas and his offer (P9-11), duty versus the life she forwent, her refusal settling "into her until it was simply a fact about her" (P13). The Tomas doorway scene is ch02's own dramatisation, not a reference to a later chunk.
- Voice/tone/POV/tense: PASS — third-person limited on Maren, past tense, unchanged.
- §7 canon continuity, incl. relief-keeper fact: PASS — Tomas at 38 (P9), scald mark at 26 (P3), both within the 19-41 window. P7's "told the relief keeper who came for her fortnight off each summer" and P11's "the authority would send a relief keeper within the month" both affirmatively depict relief coverage during and after her tenure, consistent with §7; nothing claims the station sat untended across the twenty-year span.
- Pacing / no re-staging: PASS — single chunk, no repetition of a prior scene (none exists yet to repeat).
- Shows rather than states interiority: PASS — "had felt, obscurely, that it served the sill right," "as the body knows a thing before the mind consents to it" are physical/sensory framings, not bald emotion labels.
- No contradictions with spec: PASS.
- Ambiguity preserved: PASS — no naming/confirming the listener; "a private arithmetic laid beneath the public one" stays fully unresolved.
Learnings appended: no (clean pass; revision confirms the §5c fix did not disturb reveal ownership or any other §5b criterion).

## chunk-03 — attempt 2 — 2026-08-30 00:00
Verdict: FAIL
Checked against: spec.md §5b editorial criteria, Spec-Version 4 revision pass (run 02), focused on the relief-keeper fix and reveal ownership (mechanical gates §5a re-passed: 1047 words, zero em/en-dashes, prose-only, UK spelling, "backwards" now consistent, "the way" construction thinned to 1 occurrence at P9; zero second-person hits to adjudicate)
Findings:
- Relief-keeper continuity (§7, focus check 1): PASS, and the run-01 defect is genuinely fixed. Revised P13 now reads "Other hands had kept them, decade upon decade, weather entered in the margin and the public times set down where they should be, everything a log ought to hold, faithfully... But the second discipline was not in them... Only the last handful of pages, thin and recent, held no hand at all, their place taken by a grey box." This states plainly that relief keepers filled the books faithfully across decades and only lacked the *second* (secret) discipline, with the human-hand gap confined to "the last handful of pages" (matching the ~3-year automation window). Nothing anywhere in the chunk claims or implies the station, cottage, or books were untended, unmanned, or unfilled across the twenty-year span. The old "no keeper here to fill them, only a grey box" phrasing (which read as a longer unmanned gap) is gone.
- Reveal ownership (§4 ledger, focus check 2): FAIL. The chunk correctly lands its own beat in P5 ("It was not a keeper's log. It had never been a keeper's log, not really... the light's true work was not warning ships" is not stated in those exact words, but the discovery clearly establishes it). The problem is the closing line of P15: "outside the light went round and round on its schedule, faithful to the letter of the thing and deaf, she understood now with a certainty she could not have defended to anyone living, to whatever the letter had only ever been a way of writing down." This is a close paraphrase of the ch06-owned beat verbatim from §7 canon ("the automation reproduces the public characteristic but not the true rhythm; the watch has therefore effectively lapsed"): "faithful to the letter" = keeps the public pattern, "deaf... to whatever the letter had only ever been a way of writing down" = does not carry the true rhythm. The hedge ("a certainty she could not have defended") softens *whether Maren is right*, not *whether the claim is stated* — the proposition itself (the present, automated light keeps the surface but not the substance) is delivered explicitly here, pre-empting ch06's "examines the new machinery and understands it cannot do what she did." This is the same category of defect as run-01's ch02-pre-empts-ch03 problem the orchestrator flagged this pass for. P13's related clause ("which had never made a mark of its own kind either, because it had no way of knowing one was wanted") is defensible on its own, read narrowly as "no human is physically writing in the paper ledger anymore," but it compounds the problem when read together with P15's explicit verdict on the light itself.
- On-brief row 03: PASS otherwise — the ledger discovery, the columns of timed marks, the oral unwritten notation, and the ancestral hand stretching back through the shelf all land correctly and at the right escalation point.
- Voice/tone/POV/tense: PASS.
- Pacing / no re-staging: PASS.
- Shows rather than states interiority: PASS.
- Ambiguity preserved otherwise: PASS aside from the ch06 pre-emption above — the listener itself is never named, described, or confirmed.
Learnings appended: yes — see state/learnings.md.

## chunk-03 — attempt 3 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5b editorial criteria, Spec-Version 4 revision pass (run 02), re-review of the rewrite for the attempt-2 reveal-ownership FAIL (mechanical gates §5a re-passed: 1037 words, zero em/en-dashes, prose-only, UK spelling, "backwards" consistent, "the way" construction still at 1 occurrence at P9; zero second-person hits)
Findings:
- Reveal ownership (prior FAIL): RESOLVED. P13's grey-box clause now ends "sending its clean report to a screen somewhere she had never seen" — the removed clause ("which had never made a mark of its own kind either, because it had no way of knowing one was wanted") is gone, so it no longer renders a verdict on the machine's capacity. P15 now reads "the light went round and round on its schedule, indifferent to the hand that had once kept time with it. Whatever she had spent her life recording... had never once, in all those years, been for the ships." The "indifferent to the hand" clause restates the already-established chunk-01 idea that the light does not need her (no new disclosure, and not a claim about rhythm fidelity), and the sentence's substantive claim is confined to the *historical* purpose of her own recording, ch03's own beat, with no statement about the *current* automation keeping the letter but not the substance. Ch06's beat is no longer pre-empted.
- Relief-keeper continuity (§7): PASS, retained cleanly. P13 still states relief keepers "kept them, decade upon decade... faithfully," missing only "the second discipline," with the human-hand gap confined to "the last handful of pages, thin and recent." No claim of an untended or unmanned span.
- On-brief row 03: PASS, unchanged — ledger discovery, columns of timed marks, oral notation, ancestral hand all land at the correct point on the escalation curve.
- Voice/tone/POV/tense: PASS, unchanged.
- Pacing / no re-staging: PASS, unchanged.
- Shows rather than states interiority: PASS, unchanged (the "What frightened her now" framing remains grounded in concrete elaboration, as previously assessed).
- Ambiguity preserved: PASS — the listener is never named, described, or confirmed; the chunk stops at "never been for the ships" without asserting anything about who or what it was for.
Learnings appended: no (the attempt-2 lesson already covers this case; re-review confirms the fix, no new lesson needed).

## chunk-04 — attempt 2 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5b editorial criteria, Spec-Version 4 revision pass (run 02) (mechanical gates §5a re-passed: 1012 words, zero em/en-dashes, prose-only, UK spelling, "afterwards" consistent, "the way" construction at 1 occurrence at P7; zero second-person hits)
Findings:
- On-brief row 04: PASS — the predecessor teaching scene (P1), the one rule stated explicitly ("Never break it," P3), and the answering-night (P7-9) are all present and dramatised in full, not merely deferred or summarised; this chunk genuinely owns and delivers all three.
- Reveal ownership (§4 ledger): PASS, checked against the exact forward-reach categories flagged. No mention of the current automation anywhere in the chunk, so no verdict on its fidelity (ch06's beat) is possible. No mention of Tomas anywhere in the chunk, so the vigil is not framed as the explicit reason for refusing him (ch05's beat). P11's closing clause ("whichever door she chose to leave by") is a bare, unspecific allusion to a later choice, not an explicit surfacing of ch05's content; it hints without disclosing.
- Pacing / no re-staging (run-01 sag point, ch04-06): PASS. Present-time is anchored at both ends (P1 opens grounded in the room with her hand on the book's cover; P13 closes returning to "the drawer still open, the ledgers stacked... her own hand, older now, resting on the closed cover"), and the memory itself is wholly new content (first dramatisation of the predecessor and the answering-night), not a repeat of anything shown in chunks 01-03. Earns its place.
- Voice/tone/POV/tense: PASS — third-person limited on Maren, past tense, throughout both the frame and the memory.
- §7 canon continuity: PASS — no numeric age/duration stated that could conflict with canon arithmetic; "the length of a long career and the length of the twenty years after it" is consistent. No claim about the station's staffing during or after her tenure.
- Shows rather than states interiority: PASS — "glad, in a small selfish way" and "feeling the shame of the sentence in her own mouth" are both immediately grounded in concrete context rather than left as bald labels, consistent with the pattern passed in earlier chunks.
- Ambiguity preserved: PASS, rigorously hedged throughout ("Nothing so clean as a sound," "she could never afterwards say which," "The dark took the light and gave nothing back that any instrument would have named"). The listener is never named, described, or confirmed; even the rule's implication ("something on the other side of it was capable of noticing") is framed as what the rule would require to make sense, not as confirmation that it does.
Learnings appended: no (clean pass).

## chunk-10 — attempt 2 — 2026-08-30 00:00
Verdict: PASS
Checked against: spec.md §5b editorial criteria, Spec-Version 4 revision pass (run 02), three surgical §5c fixes only (mechanical gates §5a re-passed: 922 words, zero em/en-dashes, prose-only, UK spelling — "toward" now "towards," "small competent" replaced, "the way" construction thinned from 3 to 1 occurrence at P9; zero second-person hits)
Findings:
- Coda & final ambiguity (make-or-break, focus check): PASS, confirmed undisturbed. Every recolouring survives verbatim: the horizon split into "the other one now... past the reach of any beam a lamp could throw, the one she had never seen and never would" (P9); the key recoloured as absence, closing "whether that emptiness was loss or the first honest thing she had done in a very long time" (P5); the scald-mark comma/full-stop figure, "the sentence... unfinished rather than ended" (P7). The public account "for the ships, and for no one" is quoted verbatim and reframed as true-but-incomplete (P3), correctly ch10's own beat. The final clause is unchanged and still doubly hedged: "a light... that had never lied to about anything except the one thing that mattered most" refers to the already-established §7 fact of the secret practice, not the listener's existence, and "no one, so far as she would ever be permitted to know, to receive it" asserts only the limit of her knowledge. The "long, short, long, long" finger-movement with nowhere to be sent (P9) is present and unchanged. Both readings survive intact to the final word; the listener is never named or described.
- Surgical fixes checked individually: "toward" → "towards" confirmed (P7, "towards the colour of weak tea"); "small competent" is gone, replaced by "ordinary tireless hum" (P1), no weakening of tone; "the way" thinned to the single retained instance (P9, "the way she had once held a pen above a page"), itself load-bearing and correctly kept.
- On-brief row 10: PASS, unchanged — the coda's unspectacular present-day frame, the public/private gap, and the recolourings all land as before.
- Voice/tone/POV/tense: PASS.
- §7 canon continuity: PASS — twenty years, 26, 41 all still consistent.
- Shows rather than states interiority: PASS.
- No contradictions with spec: PASS.
Learnings appended: no (clean pass; final chunk, all three surgical §5c fixes disturbed nothing).
