# Frontmatter — the structured-data layer above prose

A markdown file can carry a YAML block between `---` delimiters at the very
top, before any prose. This is not part of CommonMark or GFM — it's a
convention every tool that consumes markdown-as-data (a static site
generator, a memory system, a notes app) has independently adopted, each
with its own schema and its own rules for what happens when the schema is
violated. Four of those tools are already in active use across this vault;
this file is the one place documenting all four instead of leaving each
schema implicit in wherever it happens to be enforced.

## The four schemas already in use here

| Context | Required fields | Enforcement | What breaks it |
|---|---|---|---|
| This vault's memory files (`~/.claude/projects/*/memory/*.md`) | `name`, `description`, `metadata.type` (`user`/`feedback`/`project`/`reference`) | Convention only — no validator | A missing `description` makes the memory unfindable by future-session relevance matching; there's no error, just silent unfindability |
| Skills (`SKILL.md` frontmatter) | `name`, `description` | The harness reads these to build the skill listing | A vague `description` means the skill never gets invoked when it should — the failure is invisible until you notice the skill was never used |
| Obsidian properties (any note) | None required; special keys: `tags`, `aliases`, `cssclasses` | The Properties panel UI; unlisted vault-wide | A typo'd property key just becomes a new, separate property — Obsidian doesn't warn about near-duplicates (`tag` vs `tags`) |
| Astro content collections (`src/content/*.mdx`) | Whatever `defineCollection({ schema: z.object({...}) })` declares | **Zod, at build time** — the only one of these four that's actually type-checked | A missing required field or wrong enum value fails the build immediately, not silently |

The Astro case is the outlier worth internalizing: it's the only schema
here with a real validator, which makes it the only one where "did I get
the frontmatter right" is answered by the build rather than by careful
reading. When adding a field to an Astro-collection file, add it to the
`z.object({...})` schema in the same change — a field that exists in one
`.mdx` file's frontmatter but not in the schema is either a build error
(if the schema is strict) or silently ignored (if it isn't), and neither
is what you want.

## MDX: frontmatter plus components, in one file

MDX (`.mdx`, Astro/Next.js/Docusaurus all support it) extends markdown
with one more capability on top of frontmatter: JSX component imports and
usage, inline in the prose.

```mdx
---
title: "Project Name"
status: "live"
medium: "platform"
tags: ["Bun", "Astro", "TypeScript"]
featured: true
---

import Callout from "../../components/mdx/Callout.astro"

Regular markdown prose works exactly as normal here.

<Callout type="note">
  But a component can be dropped in wherever it's needed, receiving props
  the way any JSX component would.
</Callout>
```

This is three distinct layers in one file, and each has its own rule:

- **Frontmatter** — structured data, validated by the collection's Zod
  schema. Wrong types or missing required fields fail the build.
- **Prose** — ordinary markdown, everything in [voice.md](voice.md) and [syntax.md](syntax.md)
  applies unchanged.
- **Components** — real JSX, imported like any TypeScript import. A typo'd
  import path fails the build the same way it would in a `.tsx` file, not
  the way a markdown syntax error would (rendering broken, no error).

Don't reach for a component to do something markdown already does (a
component that just renders a styled bullet list, say) — that's adding a
build dependency and an import line for something [syntax.md](syntax.md)'s plain
list syntax already handles portably. Reach for a component when the
content is genuinely interactive or needs real logic (props, conditional
rendering, an SVG built from data) that markdown has no syntax for at all.

## The portability rule

Frontmatter is invisible to GitHub's renderer — a README with a YAML
<!-- markdownlint-disable-next-line MD044 -->
frontmatter block shows that block as literal text on github.com (GitHub
doesn't strip or render it, except specifically for Jekyll-powered GitHub
Pages sites, which is a different rendering path than the repo-file
view). Don't put frontmatter in a file whose primary audience is a human
<!-- markdownlint-disable-next-line MD044 -->
reading it on github.com; that's what a plain H1 + one-line description
([syntax.md](syntax.md)'s heading rule) is for instead.
