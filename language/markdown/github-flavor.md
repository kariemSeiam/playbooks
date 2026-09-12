# GitHub flavor — the rendering and visual layer

[syntax.md](syntax.md) and [voice.md](voice.md) cover portable CommonMark: what renders correctly
everywhere and what makes it worth reading. This file is the layer above
that — the GitHub-specific rendering extensions (GFM) and the visual
techniques built on top of them, plus the judgment calls that separate a
README that looks designed from one that looks decorated. Source: GitHub's
own documentation (`docs.github.com/.../writing-on-github`, fetched and
verified against the live docs rather than assumed from memory, since GFM
extensions have shipped new features as recently as 2022–2025), plus a
worked example (a well-executed open-source README and spec set) analyzed
for concrete technique, plus current field practice on signal-vs-noise in
badges.

**Everything here is GitHub-specific.** A file using these features renders
<!-- markdownlint-disable-next-line MD044 -->
correctly on github.com and in the GitHub mobile/desktop apps; it will
degrade (fall back to raw HTML tags, plain text, or nothing) on other
renderers — npm's package page, most IDEs' markdown preview, `cat` in a
terminal. That trade-off is usually fine for a repo's own README and docs;
know it's a trade-off, don't treat GFM as if it were portable markdown.

## The feature set

| Feature | Syntax | Renders in | Rule |
|---|---|---|---|
| Alerts | `> [!NOTE]` / `[!TIP]` / `[!IMPORTANT]` / `[!WARNING]` / `[!CAUTION]` | READMEs, issues, PRs, discussions, wikis | GitHub's own guidance: use only when crucial, 1–2 per document. An alert on every other paragraph reads as noise and the reader starts skipping all of them — the one time it's genuinely load-bearing gets skipped too. |
| Collapsed sections | `<details><summary>label</summary>` … `</details>`, add `open` to default-expanded | Everywhere GFM renders | Blank line required after `<summary>` before markdown content, or the content renders as raw text instead of formatted markdown — the single most common way this breaks. Use for: a manual table of contents, an FAQ, a secondary detail a scanning reader doesn't need on the first pass. This is the legitimate exception [syntax.md](syntax.md) already carves out for HTML-in-markdown — GFM has no native collapsible-section syntax. |
| Diagrams (Mermaid) | ` ```mermaid ` fenced block | READMEs, issues, PRs, discussions, wikis | See "Mermaid vs. ASCII" below — this is the single highest-leverage item in this file. |
| Diagrams (GeoJSON / TopoJSON / ASCII-STL) | ` ```geojson ` / ` ```topojson ` / ` ```stl ` | Same as Mermaid | Niche — a geographic map or a 3D model preview. Reach for these only when the content is genuinely geographic or a 3D asset; they're not a general diagramming tool the way Mermaid is. |
| Math | `$expr$` inline, ` ```math ` fenced block | READMEs, issues, PRs, discussions, wikis (MathJax) | Only reach for this in docs that are actually mathematical (an algorithm's complexity, a formula a reader needs to verify) — not as a way to look rigorous. |
| Footnotes | `[^1]` reference, `[^1]: text` definition anywhere in the doc | Everywhere except wikis | Prefer over a parenthetical when the aside would break the sentence's flow but the reader does want it available. |
| Task lists | `- [ ]` / `- [x]` | Everywhere | Renders as a real checkbox, and in issues/PRs the checked count rolls up into the issue/PR summary — use for actual tracked work, not as a bullet-list decoration. |
| Color swatches | `` `#RRGGBB` ``, `` `rgb(...)` ``, `` `hsl(...)` `` | **Issues, PRs, discussions only — not README/repo files.** | Renders a small color preview next to the code span. Know the scope limit before reaching for it in a design-tokens doc that lives in the repo. |
| `<picture>` for theme-aware images | `<picture><source media="(prefers-color-scheme: dark)" srcset="dark.png"><img src="light.png"></picture>` | Everywhere GFM renders | The image equivalent of this vault's own `prefers-color-scheme` convention for Artifacts — a logo or diagram that has to read on both GitHub's light and dark theme needs two exported images and this wrapper, not one image that only looks right in one theme. |
| Centering / layout | `<div align="center">…</div>`, `<p align="center">…</p>` | Everywhere GFM renders | Markdown has no native alignment. This is the justified HTML escape hatch for a logo, a badge row, or a hero tagline — not for body prose, which should stay left-aligned and readable as plain text. |
| Deliberate vertical rhythm | `<br>` between a closing `---` and the next heading | Everywhere GFM renders | GitHub collapses multiple blank lines to one when rendering; `<br>` is the only way to get intentional extra breathing room between sections. A README that alternates `---` / `<br>` / content is treating the page as designed, not just as rendered markdown. |
| Badges | Markdown image syntax pointing at a badge-generator URL (shields.io is the de facto standard: `https://img.shields.io/badge/...` or a live endpoint like `https://img.shields.io/npm/v/<pkg>`) | Everywhere GFM renders | See "Signal vs. vanity badges" below. |
| ASCII wordmark / logo | A fenced ` ```text ` block of block-letter ASCII art, usually inside `<div align="center">` | Everywhere, including a plain-text terminal `cat` | Trade-off, not a default: diffable, copy-pasteable, renders even with no image support, but fragile to hand-edit (see the alignment lesson below) and lower visual fidelity than a real logo image. Justified for a strong, deliberate brand identity; not a default choice for every project. |

## Mermaid vs. ASCII — pick correctly, don't default to ASCII

Hand-drawn ASCII box diagrams are fragile: renaming one label, or widening
one word, silently breaks every alignment in a nested box without any error
— the renderer just shows a crooked diagram, with no warning. This is not
theoretical: it happened in this vault's own work, twice, on the same
diagram, before being caught by a byte-width check written specifically to
catch it.

Mermaid removes the entire failure class for anything beyond the simplest
flow: the renderer computes layout, so relabeling a node cannot misalign a
box. The rule this earns:

- **Mermaid** for anything with branches, nesting, more than ~4 boxes, or
  that will be edited again later (architecture diagrams, sequence flows,
  state machines, ER diagrams, decision trees).
- **ASCII** only for a short, linear, effectively-final flow (`A → B → C`),
  or specifically when the file must remain legible with zero rendering at
  all — piped through `cat`, opened in a plain-text editor, read by a tool
  that strips markdown. If you reach for ASCII for anything more complex
  than that, and it isn't for the plain-text-legibility reason, that's the
  wrong default — use Mermaid.
- If ASCII is chosen anyway, verify every bordered box's line width
  programmatically before shipping it (a one-line script comparing
  `len()` of every row) rather than trusting it by eye — eyeballing
  monospace alignment across dozens of characters is exactly the failure
  mode above.

## Signal vs. vanity badges

A badge earns its place when it answers a question the reader would
otherwise have to go check for themselves: is CI passing right now, does
the published version match this README, what license, how many weekly
downloads. Three such badges in one line add real credibility and cost one
line.

A badge that doesn't answer a question — "Made with ❤️", "PRs Welcome",
"100% Pure JavaScript" — doesn't inform, it decorates, and a row of these
signals a templated README rather than a maintained one, which is the
opposite of the intended effect. The test before adding any badge: does it
tell the reader a fact they'd otherwise have to look up? If not, cut it.

Third-party dynamic badges (visitor counters, GitHub stats cards, typing
animations) pull from an external service on every render — weigh that
against the actual project this is documenting; a live production service's
README is not the place for a decorative dependency on an unrelated third
party's uptime.

## Anchors and manual tables of contents

GitHub auto-generates an anchor for every heading (lowercase, spaces →
hyphens, punctuation stripped) and, from two or more headings, a clickable
outline in the file-view UI — a manual table of contents is often already
redundant with that built-in outline. When a manual ToC earns its place
anyway (a long spec, a README with many sections, a document meant to be
skimmed before that built-in outline is easy to find), the `<details>`
collapsed-section pattern keeps it out of the way of a reader who doesn't
need it: `<summary><strong>Table of Contents</strong></summary>`, one blank
line, then the list of `[Section](#section-anchor)` links.

For a heading that needs a stable link independent of its exact wording (so
renaming the heading later doesn't break existing links to it), use a
custom anchor instead of relying on the auto-generated one:
`<a name="stable-id"></a>` directly above the heading.

## Worked example

A well-run README pairs most of the above deliberately: a shields.io row
with real-signal badges only (license, protocol, npm version, runtime
version — no vanity badges), a `<details>` collapsed table of contents,
GFM alerts used sparingly (twice in a 450-line file is a reasonable
ceiling), and a before/after ASCII diagram pair (short enough — three
lines each — that the fragility risk above doesn't apply). A `spec/`
folder run the same way is a second worked pattern worth knowing
independent of visual styling: numbered spec files, an index that states
an explicit reading order and an estimated read time for a specific
reader goal, and an `archive/` directory for superseded specs that the
current index explicitly points to rather than silently deleting.
