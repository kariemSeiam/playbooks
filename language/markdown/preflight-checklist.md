# Preflight checklist — run before calling any non-trivial `.md` file done

A how-to guide, per [document-types.md](document-types.md)'s own framework — steps only, no
re-argued reasoning here. The reasoning behind each step lives in
[syntax.md](syntax.md), [voice.md](voice.md), [document-types.md](document-types.md), and [for-agents.md](for-agents.md); read
those once, then use this list per-file afterward.

## 1. Name the document type

One word: tutorial, how-to, reference, or explanation (`document-
types.md`). If the honest answer is more than one, split the document
before writing further, not after.

## 2. Front-load the answer

Read the first sentence of the document, and the first sentence of every
section, in isolation. Does each one already carry the point, or does it
build up to something later? If it builds up, move the point to the
front and let the rest support it.

## 3. Check the heading outline alone, with no body text

Read only the headings, top to bottom. Do they alone convey what the
document contains? If the outline doesn't make sense without the prose
underneath it, the structure isn't carrying its share of the meaning yet.

## 4. Run the voice test

Strip the formatting mentally (or actually, in a scratch copy) — bold,
tables, headers, lists — and read the remaining prose as plain text. Does
it still say something specific, or does it collapse into filler the
moment the formatting stops doing the work of looking organized?

## 5. Check syntax mechanics

- One H1, ATX style, heading levels increment by one.
- Every fenced code block has a declared language.
- Every link has descriptive text, never "here" or a bare URL.
- Every mention of another file in this repo is a real relative link
  (filename as text, not the full path) — not backtick-styled text that
  only looks like it points somewhere. Grep for `` `[\w./-]*\.md` `` and
  check each hit: should this be `[FILENAME.md](path)` instead? Verify
  the target actually exists and is tracked (`git ls-files`) before
  linking — a gitignored file stays plain text, it would 404 for anyone
  else.
- Tables used only for genuinely tabular data, not for content that's
  actually a list wearing a grid.
- No trailing whitespace, no more than one consecutive blank line, file
  ends with exactly one newline.

## 6. If this file will be loaded routinely (memory, context, a playbook)

- State its size/line budget explicitly, and what happens when the
  budget is hit (archive rule, trim rule) — not just the number.
- Confirm it's reachable from somewhere already-loaded (a pointer line in
  `CONTEXT.md`, a reference from a sibling file) — an unreferenced file
  in this vault's own structure is invisible the same way an unreferenced
  tier-3 appendix is ([for-agents.md](for-agents.md)).
- If it's genuinely a reference/explanation file meant to be dipped into
  rather than read start to end, confirm the outline (step 3) supports
  jumping straight to the relevant section.

## 7. Cross-reference check

If this file restates a fact or a rule that already lives in another
file, stop — link to the canonical file instead of duplicating it. Two
copies of the same rule are a guarantee they'll eventually disagree.

## 8. If this file targets GitHub rendering (a README, a repo doc)

- Any diagram with branches, nesting, or more than ~4 boxes: Mermaid, not
  <!-- markdownlint-disable-next-line MD044 -->
  hand-aligned ASCII ([github-flavor.md](github-flavor.md)). If ASCII was used anyway,
  verify every bordered box's line width programmatically, not by eye.
- Any badge: does it answer a question the reader would otherwise look
  up (build status, version, license), or is it decorative? Cut the
  decorative ones.
- Any `> [!NOTE]`-style alert: at most one or two in the whole document.
