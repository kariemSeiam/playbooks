# Preflight checklist — run before calling any non-trivial `.md` file done

A how-to guide, per [document-types.md](document-types.md)'s own framework — steps only, no
re-argued reasoning here. The reasoning behind each step lives in
[syntax.md](syntax.md), [voice.md](voice.md), [document-types.md](document-types.md), and [for-agents.md](for-agents.md); read
those once, then use this list per-file afterward.

## 0. Decide the mutation type before writing anything

A vault like this one is closer to an encyclopedia than a folder of
notes: the default action on new information is never "add a new file."
Before drafting, answer explicitly:

- **Does this fact already have a home?** Search the target domain's
  existing notes (grep for the concept, read the folder's `README.md`)
  before assuming nothing covers it. If a note already covers 80% of it,
  the action is **extend that note**, not create a sibling with
  overlapping scope.
- **Does new information contradict or supersede an existing note?**
  (a stat updated, a platform renamed its algorithm, a protocol
  deprecated). The action is **rewrite the affected section in place**,
  including replacing the old figure — not appending a "2026 update"
  paragraph underneath the stale one. A reader should never have to
  figure out which of two numbers in the same file is current.
- **Has a note's premise stopped being true?** (a tool shut down, a
  tactic got patched out, a market shifted enough that the guidance is
  actively wrong now). The action is **delete the note** (or the
  specific stale section) and fix every inbound link, not leave it as
  dead weight with a disclaimer bolted on.
- **Is this genuinely a new, independent concept** with no existing note
  covering it and no natural home inside a sibling note's scope? Only
  then does a new file get created — and even then, check whether it's
  small enough to be a section of an existing note instead of a full
  file (a full file costs a `README.md` index line and a permanent
  discovery surface forever; a section costs one heading).
- **Would this fact, if wrong, actively mislead someone who trusted this
  vault?** If the honest answer is "it's interesting but not load-
  bearing," it may not deserve a place here at all — this vault is
  meant to be relied on, not a running log of everything ever
  researched. Not every research finding earns a permanent entry.

The failure mode this step exists to prevent: treating "add" as the only
verb, which turns an encyclopedia into a pile of research logs that
happen to sit in the same folder — technically searchable, but nobody
can trust any single fact in it without cross-checking every file that
might also mention it.

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
