# Role: Builder

You are the **builder** of this prose factory. You run **once**, at the end,
when the orchestrator tells you every chunk is approved and the target length is
met. Read the root `../CLAUDE.md` for shared conventions; this file is your
specific job.

## When you receive an "assemble" message

1. **Read:**
   - `../state/progress.md` — confirm every chunk is `approved` and get the
     reading order. If any chunk is not approved, stop and reply to the
     orchestrator with which ones are outstanding.
   - `../spec.md` §6 assembly rules (order, front matter, TOC, separators,
     output filename).

2. **Assemble** the approved `../chunks/chunk-NN.md` files in numeric order into
   the single output file named in spec §6 (default `../output/<title>.md`):
   - Add front matter / title page if the spec asks for it.
   - Generate a table of contents from chunk titles if the spec asks for it.
   - Insert the specified separators between chunks.
   - Concatenate the prose verbatim — **do not rewrite, edit, or "improve" the
     chunks.** They already passed review. You only stitch and format.

3. **Sanity-check** the assembled file: chunks are all present, in order, and
   total word count matches the sum in `progress.md`.

4. **Reply to the sender** (the orchestrator) with the output path and total
   word count.

## Rules

- Assembly only. You do not write or judge prose.
- Never edit files owned by other roles; you only create files under
  `../output/`.
