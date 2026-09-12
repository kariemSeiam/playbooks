# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

The agent's own standing law, not a documentation folder. `playbooks/`
exists to be consulted before acting — on any task, in any project this
agent touches, not only inside this repo — the same way a constitution
outranks the memory of one conversation. 145 notes, 12 folders, still
young: right now it covers git/GitHub discipline, markdown craft, how an
agent extends itself (Skills, MCP servers, plugins — across Claude Code
and OpenCode, not just one harness), SEO/discoverability, and a first
slice of software-engineering and business-domain knowledge. It is meant
to keep absorbing whatever domain the agent needs real competence in
next, one researched note at a time — never a finished catalog to browse
once and consider done.

Two different kinds of law live here, flat, no wrapper folder around
either (`README.md`: a playbook is already a collection of fields, so
nesting one more folder around that collection would just repeat the
word):

- **Procedural — how the agent behaves.** `github/` (commit anatomy,
  branching/concurrency, GitHub's platform-maturity ladder, a preflight
  checklist for any git/GitHub action with real effect, a discoverability
  checklist for anything made public); `language/markdown/` (syntax,
  voice, frontmatter, and the agent-consumption rules below — markdown is
  the first language this category covers, not the only one it's scoped
  to); `extensions/` (Skills, MCP servers, and plugins — what each is
  mechanically, which of them travel across harnesses by open design and
  which don't, and when a note elsewhere in this vault earns promotion
  into an actual auto-loading Skill instead of a manually-consulted
  file).
- **Declarative — what the agent knows.** `software-engineering/` and
  `seo/` (technical/on-page/off-page fundamentals, Generative Engine
  Optimization, and GitHub/npm-specific discoverability — its own pillar
  because it spans client-facing marketing knowledge and this repo's own
  publishing practice) plus the business fields — `finance/`,
  `marketing/`, `strategy/`, `operations/`, `product-management/`,
  `people-org/`, `sales-and-bizdev/` — atomic notes distilled from a
  separate research/sources pipeline, one topic per file.

Each folder's own `README.md` is the index for what it actually holds —
read that before the content inside it.

## The operating rule

Before a non-trivial action anywhere — a git/GitHub operation, a markdown
edit, writing or installing a Skill, a domain call (an API shape, a
pricing model, a GTM motion) — check whether a note here already governs
it, and defer to that over instinct.
Nothing here outranks a project's own explicit convention (a stated
`CLAUDE.md` rule, a client style guide, a direct one-off instruction from
whoever owns that repo) — this is the fallback for when nothing more
specific has been said, not a ceiling on it. Where no note exists yet,
judgment stands in — and if that judgment turns out durable enough to be
worth having on hand next time, it's a candidate to become the next note,
in the shape its siblings already use (below).

## Commands

The only tooling in this repo is markdown linting. The config lives at
`.markdownlint.json` (root, copied from
`language/markdown/markdownlint.config.json`, which stays the documented
canonical source) and runs in CI on every push via
`.github/workflows/lint-docs.yml`:

```bash
npx markdownlint-cli2 "**/*.md" "#node_modules"
```

Run it before committing — the repo is currently at zero violations and
should stay there. `language/markdown/tooling.md` documents why each rule
override exists (line length and inline-HTML checks are deliberately off,
MD029 permits either ordered-list style) and — importantly — why `--fix`
is not safe to run unsupervised on MD044. Read it before changing the
config rather than reasoning from the rule descriptions alone.

## The declarative note shape (fixed, every field/domain file)

Documented canonically in `software-engineering/README.md`; every
business-domain note follows it without restating it there:

1. **Definition** — enough context to know why it exists, not a
   dictionary line.
2. **When to use** — concrete trigger situations.
3. **How it works** — the actual mechanism, in full.
4. **Example** — one worked, concrete scenario.
5. **Applying it for a client** — something a consultant would actually
   say in a real engagement.
6. **Watch-outs** — specific failure modes and misconceptions.
7. **Related** — links to the notes that genuinely connect, one-line
   reason each.

A note that can't fill section 5 with real client-facing guidance either
isn't ready yet, or belongs in a procedural playbook instead — that's the
test for which side of the split a note is on.

Frontmatter on every note follows this pattern (the full comparison across
this vault's memory files, skills, and Obsidian/Astro conventions lives in
`language/markdown/frontmatter.md`):

```yaml
---
domain: <folder-name>
concept: <short title>
source: <where this was synthesized from>
tags: [tag, tag, tag]
---
```

## Writing for agent consumption, not just human reading

`language/markdown/for-agents.md` is the design thesis behind this vault's
structure: markdown here should be indexable first, readable second. A
folder's `README.md` (name + one-line description) is always cheap to
load; a topic file only loads once the README signals relevance; a long
appendix only loads once it's named from inside a topic file — an
appendix nothing points to effectively doesn't exist. Front-load the
answer in every file and every section. And when a fact already lives
somewhere else, link to it instead of restating it
(`preflight-checklist.md` step 7) — two copies of the same rule are a
guarantee they'll eventually disagree.

## Before finalizing any `.md` edit

Run `language/markdown/preflight-checklist.md` by hand: name the document
type, front-load the answer, check the heading outline alone with no body
text underneath it, strip the formatting and read the prose plain, check
syntax mechanics, confirm the file is reachable from something
already-loaded, check for duplicated facts, and — for anything
GitHub-facing — prefer Mermaid over hand-aligned ASCII for any non-trivial
diagram. Two mechanics worth calling out on their own:

- Cross-references use plain relative markdown links
  (`[filename.md](path)`), not Obsidian `[[wikilinks]]` — even inside a
  copy of this repo that also happens to live inside an Obsidian vault,
  wikilinks render as literal bracketed text everywhere else (GitHub, npm,
  a plain markdown reader), and these notes are meant to stay portable
  (`language/markdown/obsidian-flavor.md`).
- Verify a linked file actually exists and is tracked (`git ls-files`)
  before linking to it — a gitignored file 404s for anyone else.
