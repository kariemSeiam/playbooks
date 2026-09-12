# llms.txt — the machine-facing index, as an actual spec

[for-agents.md](for-agents.md) argues that markdown written for an agent's own future
consumption should be structured differently from markdown written for a
human. `llms.txt` (the convention at `llmstxt.org`, proposed 2024) is that
argument turned into a real, published spec with a fixed shape — worth
knowing as law rather than reconstructing from instinct each time, which
is exactly what happens when a project's `docs/llms.txt` gets written
from instinct, with no reference to check it against.

## The required shape

```markdown
# Project Name

> A short summary — the one paragraph containing everything necessary
> to understand the rest of the file.

Optional free-form context: paragraphs or lists, but not more headings —
the H1 and blockquote are the only required elements; this section, if
present, stays prose-only.

## Docs

- [Quick start](https://example.com/quickstart): one-line description
- [API reference](https://example.com/api)

## Optional

- [Advanced config](https://example.com/advanced): skip this if a
  shorter context is all that's needed
```

The rules, in order: **H1** (project/site name — the only strictly
required element) → **blockquote** (the one-paragraph summary an agent
should have even if it reads nothing else) → optional prose (no
headings) → **H2-delimited sections**, each a markdown link list, each
link optionally annotated with `: description`. A section literally
titled `## Optional` is a convention for marking links an agent can skip
under a tight context budget — the spec's own version of this
playbook's tier-1/tier-2/tier-3 idea ([for-agents.md](for-agents.md)), expressed as an
actual machine-parseable signal instead of a design principle.

## Two legitimate shapes, not one

- **`llms.txt`** — a curated table of contents: links out to the real
  docs, kept short specifically so an agent can decide what's worth
  fetching before paying for it. Right for a documentation site with many
  pages.
- **`llms-full.txt`** (community convention, not part of the core spec)
  — the same opening (H1 + blockquote) but with content inlined directly
  under each section instead of just linked out. Right when the whole
  thing is naturally one page's worth of facts that would cost more
  round-trips to link out than to just include — a single MCP server's
  tool catalog, for instance.

An MCP server's `docs/llms.txt` is a common instance of the second shape:
correct H1 + blockquote opening, but its `##` sections inline full tool
descriptions rather than linking to separate pages, because the entire
catalog *is* the content — there's no separate doc site to link into.
That's a legitimate
adaptation of the spec's intent, not a violation of it; the violation
would be inlining full content while still calling it `llms.txt` when a
`llms-full.txt`-labeled file would set the right expectation. Name the
file for which shape it actually is when both might plausibly exist for
the same project.

## Where it lives

At the site or API root: `/llms.txt` (and `/llms-full.txt` if both
shapes exist), fetchable as a plain file — a `GET /llms.txt` HTTP
endpoint is the right pattern for a server that has no separate
static-hosting story. For a plain GitHub repo, `docs/llms.txt` in the
repo root's `docs/` folder, cross-linked from the README's documentation
index the same way every other doc in that index already is.
