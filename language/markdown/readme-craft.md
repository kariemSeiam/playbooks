# README craft — structure and rhetoric, not rendering mechanics

[package-readme.md](package-readme.md) covers where a README's markup survives or breaks
(GitHub vs. a registry page); this file is the other half — what makes a
README's *structure* actually work for a reader deciding, in the first
few seconds, whether to keep reading.

## A nav line beats a Table of Contents, below a certain size

[github-flavor.md](github-flavor.md) already covers a `<details>`-collapsed TOC for a
README long enough to need real navigation. Below that size, a single
bold line of anchor links directly under the tagline does the same job
for less: `**[Quickstart](#quickstart) · [Why](#why) · [Configuration](#configuration)**`.
No heading, no vertical space spent, still gives a scanning reader the
shape of the whole document before they've read a word of it. Reach for
the `<details>` TOC once the section count outgrows what fits on one line
without wrapping awkwardly.

## The anti-pattern comparison table

The most persuasive device available for a README's "why this exists"
section is a two-column table: *"Instead of… / You get…"*, one row per
capability. Each row names the naive or common approach first, then the
actual one, in the same breath — the contrast does the arguing, instead
of a paragraph asserting "this is better" and expecting the reader to
take it on faith. This is the concrete, reusable shape of
[voice.md](voice.md)'s scannable-first principle applied to a persuasion problem
specifically: a claim with its counter-example sitting right next to it
is checkable at a glance; a claim alone is not.

## `<details>` as tier-2→tier-3 inside a single reference table

[github-flavor.md](github-flavor.md) already names `<details>`'s legitimate uses (a manual
TOC, an FAQ, "a secondary detail a scanning reader doesn't need on the
first pass"). The same mechanic extends one step further: a reference
table gives the one-line answer for every item (tier 2), and any row that
needs deeper mechanism gets its own `<details>` block immediately below
the table (tier 3) — so scanning the table alone is already useful, and
drilling into one specific row costs nothing to a reader who doesn't need
it. This is [for-agents.md](for-agents.md)'s cover/chapter/appendix thesis, implemented
as literal markdown structure in one file instead of split across
separate files — worth reaching for when the appendix-worthy detail is
short enough that a whole separate file would be overkill, but long
enough that inlining it into the table would break the table's
scannability.

## FAQ as pre-empted objections, not restated features

A good README FAQ doesn't restate what the earlier sections already
say — it answers the specific skepticism a real prospective adopter
would raise before trusting the project: is the free tier actually free,
does this work outside one narrow use case, why not just do this the
obvious way instead of adopting a dependency. Write the FAQ last, after
everything else, by asking "what would make me hesitate to adopt this"
rather than "what haven't I said yet" — a manufactured question restating
a feature is easy to spot and teaches the reader nothing a real objection
wouldn't have taught better.

## Every badge should answer a due-diligence question

[preflight-checklist.md](preflight-checklist.md)'s own rule: cut a badge unless it answers a
question the reader would otherwise look up. CI status answers "is this
maintained." A security-scan badge answers "is this safe to add." A
license badge answers a real legal question. A minimum-runtime-version
badge answers "what do I need to run this." If a candidate badge doesn't
map to a real question like one of these, it's decoration — cut it.

## Related

- **[package-readme.md](package-readme.md)** — the rendering-compatibility half of README
  craft; read both before writing one meant for npm/PyPI as well as
  GitHub.
- **[github-flavor.md](github-flavor.md)** — the `<details>` mechanics this file builds a
  specific pattern on top of.
- **[for-agents.md](for-agents.md)** — the tiering theory a single-file `<details>`
  reference table is one more concrete implementation of.
