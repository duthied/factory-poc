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
