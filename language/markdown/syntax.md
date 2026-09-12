# Syntax — the mechanical layer

This is what a linter would check, stated as a standard to write to rather
than a list of violations to avoid. Every rule here has a reason; if the
reason doesn't apply in a specific case, the rule can bend — but know
which one you're bending and why, don't drift into inconsistency by
accident. Source: Google's developer documentation style guide and the
`markdownlint` rule set (50+ rules, the closest thing to a full
enumeration of markdown mechanical mistakes).

## Headings

- **ATX style (`#`, `##`), never Setext (`===`/`---` underlines).** Setext
  only supports two levels and doesn't fit the rest of the heading syntax
  — needless inconsistency for no benefit.
- **Exactly one H1 per document, at the very top.** It's the document's
  title; a second one means the document doesn't know what it's about.
- **Increment by exactly one level at a time** (H2 → H3, never H2 → H4).
  Skipping a level breaks the document outline a reader (or a tool
  building a table of contents) relies on.
- **Every heading — including sub-sections — gets a unique, fully
  descriptive name.** Anchors are generated from heading text; two
  headings with the same words in different sections produce colliding or
  ambiguous anchors, which breaks the one thing headings are for beyond
  visual structure: being a linkable, addressable location.
- **A space after the `#`, and a blank line before and after the
  heading.** Purely a source-readability rule, but it's free and it's
  universal — no reason to skip it.
- **No trailing punctuation in a heading.** A heading is a label, not a
  sentence.

## Lists

- **One consistent bullet marker per document** (pick `-` and keep it).
  Mixed markers read as noise, not signal.
- **For ordered lists that will be edited over time, all-`1.`** (let the
  renderer number them) rather than hand-numbering every item — hand
  numbering is the thing that goes stale first when an item is inserted
  or removed later. For a short, stable list, sequential numbers are fine
  and slightly more readable in source.
- **Blank line before and after a list**, and consistent indentation (a
  fixed number of spaces, not tabs, not "whatever lined up in this
  editor") for nested content — inconsistent indentation is the single
  most common reason a renderer merges a list with surrounding text or
  breaks nesting silently.

## Code

- **Fenced code blocks (` ``` `), never indented-by-four-spaces blocks.**
  Indented blocks can't declare a language, have no unambiguous start/end
  marker, and don't get syntax highlighting anywhere. There is no
  remaining reason to use them.
- **Always declare the language on a fenced block** (` ```bash `,
  ` ```yaml `, ` ```text ` if genuinely plain) — without it, every
  renderer and every future reader has to guess, and guesses are
  sometimes wrong in ways that look like a rendering bug rather than a
  missing hint.
- **Inline code (single backticks) for anything that is literally code**:
  identifiers, file paths, commands, flags, literal values — not for
  emphasis. Emphasis has its own syntax; using code formatting for
  emphasis (or vice versa) means a reader can no longer trust either
  convention to mean what it says.

## Links

- **Descriptive link text, never "here" / "click this" / a bare URL as
  the visible text.** Readers scan for the parts of a document that catch
  the eye — links are exactly that — and a link that reads "here" tells a
  scanning reader nothing about where it goes or why to follow it.
- **Relative paths for links within the same directory/repo; avoid `../`
  chains that climb out of it.** A same-directory relative link survives
  a repo being moved or renamed; a multi-level `../../` chain is fragile
  in exactly the way that breaks silently months later.
- **Reference-style links** (`[text][ref]` with the `[ref]: url` defined
  once near the end of the section or document) **when a URL is long
  enough to disrupt reading the sentence it's in**, especially inside
  tables, where an inline raw URL blows out column width for every row.
- **A reference to another file in the same repo is a link, not inline
  code.** Writing `` `docs/QUICKSTART.md` `` looks like it points somewhere
  but doesn't — backtick formatting signals "this is literal text or an
  identifier," never "click here," so on GitHub it renders as inert
  styled text. If the sentence names a file the reader could plausibly
  want to open next, make it `[QUICKSTART.md](docs/QUICKSTART.md)` — a
  real relative link, found and verified against the actual file it's
  referencing, not typed from memory and trusted.
  - **Link text is the filename with its extension, not the full path.**
    The path belongs in the href; repeating `docs/` in the visible text
    for every link in a `docs/`-relative table or list is noise the
    reader has already inferred from context, once.
  - **Exception: don't link to a file that isn't actually tracked and
    pushed.** A reference to a gitignored file (a private memory note, a
    local-only config) must stay as plain backtick text — linking to it
    produces a dead link the moment anyone else opens the repo on
    GitHub, because the target was never there for them. Check `git
    ls-files` before linking, don't assume from the file existing
    locally.
  - **Exception: a document doesn't link to itself.** A changelog entry
    or index row that names "this file" stays plain text; a self-link is
    functionally a no-op that only adds visual noise.

## Tables

- **Use a table only for genuinely tabular data** — rows that share the
  same columns, where a reader benefits from scanning down one column
  across many rows. If what's being expressed is a sequence of related
  points rather than a grid, a list is easier to both write and read; the
  temptation to reach for a table because it "looks more organized" is
  usually building structure the content doesn't actually have.
- **Consistent column count across every row**, and pipe alignment
  doesn't need to be visually perfect in source (renderers don't care) —
  don't spend effort padding pipes with spaces to line up visually if the
  content changes often; do keep it neat for tables that are effectively
  finished and rarely edited, since source readability still matters.

## Images

- **Sparingly.** Plain text gets a reader to the point faster with less
  friction; an image is justified when the thing being communicated is
  inherently visual (a layout, a diagram, a screenshot of an actual UI
  state) — not as decoration.
- **Always with descriptive alt text.** A reader using a screen reader, or
  a tool (including an agent) that only sees text, gets nothing from an
  image with no alt text — the content effectively doesn't exist for them.

## Whitespace and file hygiene

- **No trailing whitespace on any line.**
- **File ends with exactly one trailing newline**, no more.
- **No more than one consecutive blank line** — extra blank lines are
  noise that additionally renders inconsistently across tools.

## HTML inside markdown

- **Avoid it unless markdown genuinely cannot express the structure
  needed** (a specific multi-row/multi-column table layout, a detail/
  summary collapsible section where the platform doesn't support a
  markdown-native equivalent). Every HTML escape hatch reduces the
  document's portability across renderers and its readability in raw
  source — the two properties markdown exists to protect in the first
  place.
