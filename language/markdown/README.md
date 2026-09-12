# Markdown playbook — read before writing any `.md` file

This is standing law for writing markdown itself — not about any one
topic (that's what `playbooks/github/` and future topic playbooks are
for), but about the craft of the document as an artifact: structure,
syntax, voice, and — the reason this exists as its own playbook rather
than folded into general writing advice — the fact that a large fraction
of what gets written here is read by an AI agent (a future session of
mine) at least as often as by a human, and that readership has different
needs than either alone.

Researched from primary sources, not improvised: Google's developer
documentation style guide, the `markdownlint` rule set (the closest thing
to an exhaustive list of what's technically wrong with a markdown file),
the Diátaxis documentation framework, the Microsoft Writing Style Guide,
the GitHub Flavored Markdown spec, and the "progressive disclosure" /
book-pattern literature on writing documentation for agent consumption.
None of it is reproduced as a report here — it's distilled into law, with
the reasoning kept and the source noted where it matters.

## Files in this playbook

- [syntax.md](syntax.md) — the mechanical layer: headings, lists, code blocks,
  links, tables, images, whitespace. What markdownlint would flag, stated
  as a positive standard rather than a list of violations.
- [voice.md](voice.md) — the prose layer: scannable-first, active voice, plain
  language, and why a well-tuned AI agent's existing "no filler" pact is
  the same principle every technical-writing style guide converges on
  anyway.
- [document-types.md](document-types.md) — which of the four kinds of document this is
  (tutorial, how-to, reference, explanation — Diátaxis's distinction), why
  mixing them produces documents that serve nobody well, and how each of
  an AI agent's own file types (`CONTEXT.md`, `MEMORY.md`, a playbook,
  `ACTIVE.md`) maps onto the framework.
- [for-agents.md](for-agents.md) — the one genuinely non-obvious finding: markdown
  written for an AI agent's own future consumption should be structured
  differently than markdown written purely for a human — indexable
  first, readable second, budgeted in tokens the way a human writer
  budgets a reader's attention.
<!-- markdownlint-disable-next-line MD044 -->
- [github-flavor.md](github-flavor.md) — the GitHub-specific rendering layer on top of
  portable markdown: alerts, collapsed sections, Mermaid vs. ASCII
  diagrams, badges, theme-aware images, and the judgment calls (signal
  vs. vanity, when a visual technique earns its place) that separate a
  README that looks designed from one that looks decorated.
- [Obsidian-flavor.md](obsidian-flavor.md) — the vault-specific layer: wikilinks vs.
  markdown links, Obsidian's 13 callout types vs. GitHub's 5 (and which
  direction that compatibility runs), properties, tags. Scoped to core
  Obsidian only — no community-plugin syntax, since this vault has none
  installed.
- [frontmatter.md](frontmatter.md) — the YAML layer above prose: the four different
  frontmatter schemas already in active use across this vault (memory
  files, Skills, Obsidian properties, Astro content collections), which
  one is actually validated, and how MDX layers frontmatter + prose +
  JSX components in one file.
- [package-readme.md](package-readme.md) — what survives the trip from a GitHub repo
  page to an npm/PyPI registry page (most GitHub-only chrome doesn't),
  and the relative-link/image gotcha that specifically breaks on
  registry pages.
- [readme-craft.md](readme-craft.md) — the structural and rhetorical half of a great
  README, not the rendering half: the anti-pattern comparison table, a
  nav line instead of a TOC below a certain size, `<details>` as
  tier-2→tier-3 inside one reference table, an FAQ built from real
  objections. Mined from a real, working example, not derived in the
  abstract.
- [decision-records.md](decision-records.md) — the ADR pattern, generalized from one
  instance already adopted ad hoc in this vault's own work: when a
  decision earns a durable record, when it doesn't, the template, and
  how supersession works.
- [llms-txt.md](llms-txt.md) — the `llms.txt` spec (llmstxt.org) as actual law
  rather than instinct: required shape, the `llms.txt` vs.
  `llms-full.txt` distinction, and where the line is between adapting
  the spec's intent and just not following it.
- [tooling.md](tooling.md) + **`markdownlint.config.json`** — turns the
  mechanical half of [syntax.md](syntax.md) into something CI actually enforces,
  with every override traced back to a specific rule elsewhere in this
  playbook rather than invented, and verified by actually running it
  against this playbook's own files rather than reasoned about in the
  abstract.
- [preflight-checklist.md](preflight-checklist.md) — the concrete pass to run before calling
  any non-trivial `.md` file finished.

## The one-sentence thesis, if you read nothing else

**A markdown file has to work twice: once as a document a human can scan
in five seconds and trust, and once as a machine-parseable structure an
agent can navigate without reading it end to end** — those are usually
the same discipline (clear hierarchy, one idea per section, the answer
before the reasoning), not two competing ones, which is the actual reason
good markdown craft matters here more than in most places it's practiced.

## How to use a project-specific override

Same rule as every other playbook in this vault: a project's own stated
convention (a style guide already in its repo, an explicit instruction)
wins over this playbook's defaults. This is the fallback for when nothing
more specific has been said.
