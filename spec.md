# Spec: The Lighthouse at Kestrel Point

**Spec-Version:** 4

> Sample spec for exercising the factory end-to-end. A literary science-fiction
> novelette in ten chunks.
>
> Bump **Spec-Version** whenever a rule that affects already-written prose
> changes (voice, length, style, canon, acceptance criteria). The orchestrator
> stamps each chunk with the version it was approved under and, on startup,
> flags any approved chunk stamped with an older version as `stale` and
> re-queues it for a revision pass.
>
> **Version history.** v1: original literary short story. v2: added the
> no-em-dash rule, the impersonal-"you" clarification, and the §7 canon. v3:
> reconceived as a 10,000-word literary science-fiction work (the beacon twist);
> the earlier three-chunk literary version is archived under `archive/v2-literary/`.
> v4: codified the run-01 evaluation findings, to lift the four dimensions that
> scored 4/5 (Arc, Voice, Pacing, Prose) toward 5. Added §5c whole-work mechanical
> gates (run at assembly, before the evaluator), extended the §5a UK-spelling
> grep, added the §4 reveal ledger and §5b reveal/pacing rules, and elevated the
> relief-keeper coverage in §7 to an explicit fact with a reviewer check.

## 1. Overview

- **Working title:** The Lighthouse at Kestrel Point
- **Form:** Literary science-fiction novelette
- **One-line premise:** A retired lighthouse keeper returns to the light she
  once tended and discovers that "keeping the light" was never about the ships:
  the lighthouse is a beacon that signals to, and listens for, something in the
  deep, and her leaving twenty years ago mattered far more than she was ever
  allowed to know.
- **The twist, stated plainly (for the team, never for the reader):** the
  automation is a cover story. Generations of keepers maintained not a
  navigation characteristic but an exact inherited *rhythm* in the lamp, a vigil.
  The machine that replaced Maren reproduces the public flash pattern but not the
  true rhythm, so the watch has effectively lapsed since she left. Over her
  return she reconstructs what she gave her life to, and confronts the real
  weight of the choice she made when she refused to leave with Tomas.
- **The core stays human.** This is a story about devotion, a life given to
  something unprovable, and the cost of a choice, told through a first-contact
  premise that never resolves into spectacle. The science fiction deepens the
  original emotional question ("did I choose rightly?"); it does not replace it.

## 2. Target length (the factory's "done" condition)

- **Total target:** 10,000 words
- **Tolerance:** plus or minus 10%
- **Per-chunk target:** 900 to 1,100 words (ten chunks)

The orchestrator stops queueing new chunks once cumulative **approved** word
count reaches the target (within tolerance) and the outline is complete.

## 3. Audience & voice

- **Audience:** adult readers of literary science fiction (think the quiet,
  interior end of the genre, not action or hard-tech).
- **North star / comparables:** the restraint of Kazuo Ishiguro, the oceanic
  unease of Jeff VanderMeer, the lonely-vigil mood of a slow first-contact story.
- **Tone / voice:** warm, restrained, sensory; melancholy but not sentimental.
  The strange is delivered quietly and by inference, never as a reveal or a
  set-piece.
- **POV & tense:** third-person limited (Maren), past tense.
- **Style constraints:** UK spelling. **Never use em-dashes (the "—" character)
  or en-dashes (the "–" character).** Recast the sentence, or use commas, colons,
  or full stops instead (do not substitute a hyphen). **No second person in
  narration**, including the impersonal or gnomic "you"; use "one", recast, or
  fold it into Maren's own perception. (Dialogue may address another character
  naturally.) No headers or lists inside the prose; each chunk is continuous
  prose only.
- **Science-fiction handling (important):**
  - **No technobabble and no exposition dumps.** The premise reaches the reader
    through sensation, object, and inference, never through a character
    explaining the mechanism.
  - **Keep the ambiguity load-bearing.** The text must remain readable two ways
    at once: as a literal account of a beacon and a listener, and as the
    meaning-making of a solitary woman who gave her life to a lonely task. Never
    close that gap. Do not confirm or deny the non-human explicitly.
  - **Leave the "something" unspecified.** Deep water or deep sky is deliberately
    ambiguous; do not name, describe, or embody the listener. Its presence is
    only ever implied (a rhythm, an answer that may not be an answer, a wrongness
    in the automated log).

## 4. Structure / outline

Ten chunks, in reading order. The strangeness escalates gradually: the first two
chunks read almost purely as the v1 literary story with faint wrongness seeded
underneath; the beacon truth surfaces across the middle; the final chunks carry
its full weight without ever making it explicit.

| # | Working title | What it must cover / accomplish |
|---|---------------|---------------------------------|
| 01 | The Road Back | Maren drives to Kestrel Point after twenty years. Establish her, the coastal setting, the automated light. Seed one faint wrongness: the lamp's turning does not keep quite the rhythm she remembers. End as she reaches the door. |
| 02 | The Keeper's Room | Inside. Memory braids with the present: why she left, Tomas, duty versus the life she forwent. Seed, without stating it outright, that her nightly "logs" were kept in a private notation she followed without fully understanding. Hint that they tracked something other than ordinary weather or shipping, but leave the explicit discovery (that the records are not a keeper's log at all) to chunk 03 per the reveal ledger. |
| 03 | The Ledger | She finds the old logbooks. The records are not what a keeper's log should be: columns of timings, marks against the turning of the lamp, a rhythm handed down and never explained. First real sense that the light's true work was not warning ships. |
| 04 | The Rhythm | Memory: her predecessor teaching her the true cadence of the lamp, the one rule (never break the rhythm), and the night early in her keeping when the dark beyond the beam seemed, once, to keep time back. Establish the vigil as inheritance. |
| 05 | What She Stayed For | Tomas and the refusal, reframed. Her "no" was not only duty or love of place; leaving would have broken the watch, and she half believed, without proof, what that might cost. Her refusal of a life was a yes to something vast and unprovable. |
| 06 | The Automation's Lie | Present. She examines the new machinery and understands it cannot do what she did: it keeps the flash pattern but not the true rhythm. The listening has gone unanswered for twenty years. Her replacement kept the surface; the machine lost the substance. |
| 07 | The Thing in the Log | Rising strangeness, held ambiguous. Something in the automated record, or on the horizon, or in the sea's behaviour, reads as a response, or as the absence where a response used to be. Is it real, or is she a keeper seeing signs? Do not resolve it. |
| 08 | The Long Watch | She keeps one night watch the old way, by hand, re-establishing the rhythm. The physical and emotional toll. The vigil as devotion, gathering her whole life into a single night. |
| 09 | First Light | Dawn. The automated lamp cuts at first light. Maren makes a small, concrete choice about the key and the watch: to abandon the vigil to the machine and the unanswered deep, or to do one last true thing. Quiet, earned, not tidy. Callback to an image from chunk 01. |
| 10 | The Beacon | Coda. The consequence of her choice, ambiguous and unspectacular. The light will come on at dusk "for the ships, and for no one", but she, and the reader, now know that is the lie, and something may or may not still be listening. Recolour the grey-plate horizon, the kept key, and the scald mark from earlier chunks. |

### Reveal ledger (which chunk owns each disclosure)

The strangeness escalates only if each beat lands in its assigned chunk. **A
chunk must not disclose a beat owned by a later chunk** (in run 01, ch02
pre-empted ch03's discovery). Earlier chunks may hint or seed by inference, but
the first *explicit* surfacing of a beat belongs to its owner. The reviewer
checks this per chunk (§5b).

| Beat (first explicit surfacing) | Owner |
|---------------------------------|-------|
| Faint wrongness in the lamp's rhythm (seed only, unexplained) | 01 |
| The logs use a private notation Maren followed without understanding | 02 |
| The records are not a keeper's log; the light's work was not the ships | 03 |
| The true cadence, its oral inheritance, and the one rule (never break it) | 04 |
| The vigil as the real reason she refused to leave with Tomas | 05 |
| The automation keeps the flash but not the true rhythm; the watch has lapsed | 06 |
| A possible response, or the absence of one, held unresolved | 07 |
| The full weight of the vigil kept by hand, its toll | 08 |
| The choice about the key and the watch | 09 |
| The consequence, left open; the public "for the ships" reframed as the lie | 10 |

## 5. Acceptance criteria

Checked in two stages. The orchestrator runs the **mechanical gates** first:
they are cheap and deterministic, so a chunk that fails any of them is bounced
straight back to the writer **without spending a reviewer turn**. Only chunks
that clear the mechanical gates go to the reviewer for **editorial** judgment.
A chunk is `approved` only when both stages pass.

### 5a. Mechanical gates (deterministic; orchestrator runs these before review)

Each has a shell check the orchestrator can run against `chunks/chunk-NN.md`.
Any failure is an automatic bounce back to the writer.

- [ ] **Length** 900 to 1,100 words. `wc -w chunks/chunk-NN.md`
- [ ] **No em-dashes or en-dashes.** `grep -nP '[\x{2014}\x{2013}]' chunks/chunk-NN.md` returns nothing.
- [ ] **Prose only**: no markdown headers or list bullets. `grep -nE '^\s*(#|[-*+] )' chunks/chunk-NN.md` returns nothing.
- [ ] **UK spelling**: no common US spellings, plus the `toward`/`afterward`
  adverbs that drifted in run 01 (UK prefers `towards`/`afterwards`).
  `grep -niwE 'color|gray|harbor|honor|realize|meter|theater|traveled|neighbor|favor|toward|afterward' chunks/chunk-NN.md` returns nothing. (Grep flags candidates; a genuine proper noun is the writer's to justify. Directional words valid in both dialects, e.g. forward/backward, are left to the §5c variant-consistency check rather than bounced here.)

**Assisted check (grep surfaces candidates, reviewer adjudicates):**
- [ ] **No second person in narration.** `grep -niwE 'you|your|yours' chunks/chunk-NN.md`; every hit must be inside dialogue, and any hit in narration fails. A pure grep cannot tell narration from dialogue, so the reviewer confirms each hit.

### 5b. Editorial review (reviewer judgment)

- [ ] On-brief: covers what its outline row calls for, no scope drift, and sits
  at the right point on the escalation curve (faint wrongness early, full weight
  late).
- [ ] Voice/tone/POV/tense match §3 (third-person limited on Maren, past tense).
- [ ] Continuity: consistent with the §7 canon and all approved chunks. In
  particular, reconcile any claim about the station being unkept, empty, or
  untended against the §7 relief-keeper fact (relief keepers held it for most of
  the twenty years; it was not simply abandoned when Maren left).
- [ ] Reveal ownership: the chunk does not disclose a beat the §4 reveal ledger
  assigns to a later chunk (hinting or seeding by inference is fine; explicit
  disclosure of a later chunk's beat is a fail).
- [ ] Pacing and no re-staging: the chunk earns its place and, if it is
  memory-heavy, still advances present-time or reframes rather than repeats. A
  prior scene may be referenced but must not be re-dramatised in near-identical
  wording.
- [ ] No contradictions with the spec.
- [ ] Shows rather than states Maren's interiority (no bald emotion-labelling).
- [ ] **Ambiguity preserved:** the chunk never explicitly confirms or denies the
  non-human, never names or describes the listener, and contains no technobabble
  or exposition dump. The strange arrives by sensation and inference.

### 5c. Whole-work mechanical checks (deterministic; run at assembly, before the evaluator)

Some defects are invisible in a single chunk and only appear across the finished
whole; in run 01 these cost points on Prose, Voice, and Pacing at the eval stage.
The orchestrator runs these deterministic checks against the **assembled**
deliverable (spec §6) after the builder finishes and **before** dispatching the
evaluator. A failure re-queues the specific implicated chunks for revision (same
mechanism as an eval FAIL: note the offending lines, revise, re-review,
re-assemble, re-check), so the evaluator only ever sees a clean whole.

- [ ] **Signature-construction cap.** The "the way …" simile construction must not
  exceed roughly **1 per 800 words** across the whole (run 01 had ~38 in 9,700
  words, about 1 per 250). Count: `grep -ioE 'the way (a|the|an|she|he|it|one|his|her|they|you)?' output/<file>.md | wc -l`, compared against `wc -w`. Over the cap → flag the densest chunks for varied phrasing.
- [ ] **Distinctive-phrase repetition.** No distinctive (non-stock) phrase of 3+
  words should recur **3 or more times** across the whole (run 01: "small
  competent" ×4). Scan for repeated 3-to-5-word phrases and flag any that are
  distinctive rather than ordinary connective language.
- [ ] **Spelling-variant consistency.** No word should appear in two spellings
  across chunks (run 01: `towards` ×3 vs `toward` ×2). Flag any word present in
  both a UK and US form, or both an `-s` and non-`-s` directional form, anywhere
  in the assembled text; the writer picks one and makes it consistent.
- [ ] **Near-duplicate passage detection.** No scene may be re-dramatised in
  near-identical wording in a later chunk (run 01: the Tomas doorway was re-staged
  almost verbatim from ch02 in ch05). Flag long shared substrings or near-identical
  sentences between chunks; a prior scene may be referenced but not repeated.

## 6. Assembly rules (for the builder)

- **Order:** by chunk number, 01 through 10.
- **Front matter:** title ("The Lighthouse at Kestrel Point") as an H1 at the top; no author line.
- **Table of contents:** no.
- **Separators between chunks:** a centered `* * *` between chunks (nine in total; no chunk titles in the final text).
- **Output file:** `output/the-lighthouse-at-kestrel-point.md`

## 7. Canon (fixed facts; honour across every chunk)

Non-negotiable established facts. No new or revised chunk may contradict these;
the reviewer checks continuity against this list (§5b). Add to it as facts are
established, so continuity does not depend on re-reading every prior chunk.

### People and timeline (carried from the earlier version)

- **Maren** is 61 now. She first came to Kestrel Point at 19, became the keeper,
  and left at 41 (roughly 20 years ago); she has lived inland ever since. She
  did **not** keep the light into her late fifties.
- The lighthouse was **automated about 3 years ago**. Maren learned of it by
  letter, years after she had already left; she was long gone by then.
- **The station was NOT empty for the twenty years after Maren left.** Relief
  keepers held it for roughly the seventeen years between her departure and the
  automation about three years ago. So no chunk may describe the station, the
  cottage, or the logs as untended or unmanned across that whole span. What the
  relief keepers lost was the *true rhythm* (they kept the public light but not
  the vigil), not the physical keeping. Only the last ~3 years, under the
  machine, had no human keeper at all.
- **Tomas** arrived the spring she was 38, off a survey boat. He asked her to
  leave with him for a white house above a bay in the south (olive trees). She
  chose the light and stayed, leaving three years later at 41.
- **Recurring images** to keep consistent: the grey-plate / wet-slate horizon;
  the kept iron key; the scald mark (a pale comma) on the kitchen sill; the
  removed gate (two bare posts).

### The beacon (the science-fiction canon)

- **The light's true purpose** is a vigil: a beacon that signals to, and listens
  for, something non-human in the deep. The listener is never named, described,
  or embodied; deep water or deep sky is left ambiguous.
- **"Keeping the light"** means maintaining an exact inherited *rhythm* in the
  lamp's turning, distinct from and layered beneath the public flash
  characteristic that ships see. The rhythm is the vigil.
- **The rhythm is passed down orally, keeper to keeper**, alongside a single
  rule: never break it. The public story has always been ordinary lighthouse
  duty, then ordinary automation.
- **The automation reproduces the public characteristic but not the true
  rhythm.** The watch has therefore effectively lapsed. Maren was the last to
  keep it truly; her relief keepers kept it imperfectly, and the machine not at
  all. It has gone unanswered for the twenty years since she left.
- **Ambiguity is canon.** The text must never settle whether the listener is
  real. Both readings (literal beacon; a solitary woman's meaning-making) must
  remain fully available at every point.

## 8. Themes (what the writer should keep true)

- Devotion to something unprovable, and whether a life so spent was wasted or
  redeemed.
- The gap between the public account of a life (a keeper, then a retiree) and its
  private weight.
- Choice that cannot be re-decided, only carried. Maren's refusal of Tomas is the
  human hinge; the beacon is the scale against which its cost is measured.

## 9. Final evaluation (rubric)

After the builder assembles the deliverable **and the §5c whole-work mechanical
checks pass**, the **evaluator** judges the whole work (not individual chunks)
against this rubric and writes the result to `state/eval-report.md`. This is a
holistic pass: things a per-chunk reviewer cannot see, because they only emerge
across the seams of the finished piece. (§5c already removes the deterministic
whole-work defects, so the evaluator can focus on judgment the rubric below
calls for.)

Score each dimension **1 to 5** (5 is best) with at least one piece of cited
evidence from the text (a short quote or a chunk reference):

- **Arc & structure**: the ten-chunk escalation lands; the faint-wrongness to
  surfacing to full-weight curve holds; a genuine beginning, middle, and end.
- **Ambiguity sustained**: the beacon is never confirmed or denied anywhere in
  the whole work; no exposition dump or technobabble leaked in at any seam; both
  readings stay available start to finish.
- **Voice & POV consistency**: third-person limited on Maren, past tense, tone,
  and UK spelling hold across every chunk boundary, with no drift.
- **Pacing**: no sag in the middle; the escalation earns the coda; no chunk
  feels like filler.
- **Prose quality**: sentence-level craft and show-don't-tell judged across the
  whole, not chunk by chunk.
- **Coda & resolution**: the ending is earned and not tidy, and it recolours the
  chunk-01 images (grey-plate horizon, kept key, scald mark).
- **Thematic coherence**: the §8 themes (devotion to the unprovable, the
  public/private gap, irreversible choice) actually land as a whole.

**Verdict:** **PASS** requires an overall mean of **4.0 or higher** AND **no
single dimension below 3**. Anything else is **FAIL**.

**On FAIL:** the report must name the specific **chunks** implicated in each weak
dimension, so the orchestrator can target revisions rather than rewrite
everything. The orchestrator re-queues those chunks, the loop revises and
re-reviews them, the builder re-assembles, and the evaluator runs again. This
repeats up to **2 evaluation rounds**; if it still fails, the run is flagged
`needs-human`.
