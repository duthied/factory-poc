# Spec: The Lighthouse at Kestrel Point

**Spec-Version:** 2

> Sample spec for exercising the factory end-to-end. A short three-part story.
>
> Bump **Spec-Version** whenever a rule that affects already-written prose
> changes (voice, length, style, canon, acceptance criteria). The orchestrator
> stamps each chunk with the version it was approved under and, on startup,
> flags any approved chunk stamped with an older version as `stale` and
> re-queues it for a revision pass. (v2 added the no-em-dash rule, the
> impersonal-"you" clarification in §3, and the §7 canon.)

## 1. Overview

- **Working title:** The Lighthouse at Kestrel Point
- **Form:** Short story (literary)
- **One-line premise:** A retired lighthouse keeper returns to the automated
  light she once tended and confronts what she gave up to keep it.

## 2. Target length (the factory's "done" condition)

- **Total target:** 3,000 words
- **Tolerance:** ± 15%
- **Per-chunk target:** 900–1,100 words

The orchestrator stops queueing new chunks once cumulative **approved** word
count reaches the target (within tolerance) and the outline is complete.

## 3. Audience & voice

- **Audience:** general adult readers of literary short fiction
- **Tone / voice:** warm, restrained, sensory; melancholy but not sentimental
- **POV & tense:** third-person limited (Maren), past tense
- **Style constraints:** UK spelling. **Never use em-dashes (the "—" character)
  or en-dashes (the "–" character).** Recast the sentence, or use commas, colons,
  or full stops instead (do not substitute a hyphen). **No second person in
  narration**, including the impersonal or gnomic "you" (e.g. "what you carry
  in", "the way you know a thing"); use "one", recast, or fold it into Maren's
  own perception. (Dialogue may address another character naturally.) No headers
  or lists inside the prose; each chunk is continuous prose only.

## 4. Structure / outline

| # | Working title | What it must cover / accomplish |
|---|---------------|---------------------------------|
| 01 | The Road Back | Maren drives to Kestrel Point after 20 years. Establish her, the coastal setting, and that the lighthouse is now automated. End as she reaches the door. |
| 02 | The Keeper's Room | Inside. Memory braids with the present: why she left, the person (Tomas) she chose not to follow. Establish the central tension: duty vs. the life she forwent. |
| 03 | First Light | Dawn. Maren makes a small, concrete choice that resolves her relationship to the place. Quiet, earned, not tidy. Callback to an image from chunk 01. |

## 5. Acceptance criteria

Checked in two stages. The orchestrator runs the **mechanical gates** first:
they are cheap and deterministic, so a chunk that fails any of them is bounced
straight back to the writer **without spending a reviewer turn**. Only chunks
that clear the mechanical gates go to the reviewer for **editorial** judgment.
A chunk is `approved` only when both stages pass.

### 5a. Mechanical gates (deterministic; orchestrator runs these before review)

Each has a shell check the orchestrator can run against `chunks/chunk-NN.md`.
Any failure is an automatic bounce back to the writer.

- [ ] **Length** 900–1,100 words. `wc -w chunks/chunk-NN.md`
- [ ] **No em-dashes or en-dashes.** `grep -nP '[\x{2014}\x{2013}]' chunks/chunk-NN.md` returns nothing.
- [ ] **Prose only**: no markdown headers or list bullets. `grep -nE '^\s*(#|[-*+] )' chunks/chunk-NN.md` returns nothing.
- [ ] **UK spelling**: no common US spellings. `grep -niwE 'color|gray|harbor|honor|realize|meter|theater|traveled|neighbor|favor' chunks/chunk-NN.md` returns nothing. (Grep flags candidates; a genuine proper noun is the writer's to justify.)

**Assisted check (grep surfaces candidates, reviewer adjudicates):**
- [ ] **No second person in narration.** `grep -niwE 'you|your|yours' chunks/chunk-NN.md`; every hit must be inside dialogue, and any hit in narration fails. A pure grep cannot tell narration from dialogue, so the reviewer confirms each hit.

### 5b. Editorial review (reviewer judgment)

- [ ] On-brief: covers what its outline row calls for, no scope drift.
- [ ] Voice/tone/POV/tense match §3 (third-person limited on Maren, past tense).
- [ ] Continuity: consistent with the §7 canon and all approved chunks.
- [ ] No contradictions with the spec.
- [ ] Shows rather than states Maren's interiority (no bald emotion-labelling).

## 6. Assembly rules (for the builder)

- **Order:** by chunk number.
- **Front matter:** title ("The Lighthouse at Kestrel Point") as an H1 at the top; no author line.
- **Table of contents:** no.
- **Separators between chunks:** a centered `* * *` between chunks (no chunk titles in the final text).
- **Output file:** `output/the-lighthouse-at-kestrel-point.md`

## 7. Canon (fixed facts; honour across every chunk)

Non-negotiable established facts. No new or revised chunk may contradict these;
the reviewer checks continuity against this list (§5b). Add to it as facts are
established, so continuity does not depend on re-reading every prior chunk.

- **Maren** is 61 now. She first came to Kestrel Point at 19, became the keeper,
  and left at 41 (roughly 20 years ago); she has lived inland ever since. She
  did **not** keep the light into her late fifties.
- The lighthouse was **automated about 3 years ago**. Maren learned of it by
  letter, years after she had already left; she was long gone by then.
- **Tomas** arrived the spring she was 38, off a survey boat. He asked her to
  leave with him for a white house above a bay in the south (olive trees). She
  chose the light and stayed, leaving three years later at 41.
- **Recurring images** to keep consistent: the grey-plate / wet-slate horizon;
  the kept iron key; the scald mark (a pale comma) on the kitchen sill; the
  removed gate (two bare posts).
