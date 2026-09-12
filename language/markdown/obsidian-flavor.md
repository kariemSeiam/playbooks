# Obsidian flavor — the vault-specific layer

Parallel to [github-flavor.md](github-flavor.md), for the same reason: this vault is itself
an active Obsidian vault (`.obsidian/` at its root), and Obsidian's
markdown dialect diverges from both portable CommonMark and GitHub's GFM
in ways worth knowing before writing a note
that's meant to actually live and link inside it. Verified against
Obsidian's own help docs, scoped deliberately to **core Obsidian only** —
this vault has no community plugins installed (no Dataview, no Templater,
nothing beyond Obsidian's built-in feature set), so plugin-specific syntax
like Dataview query blocks is out of scope here on purpose. If a plugin
gets installed later, it earns its own section then — not before, on
spec.

## Wikilinks vs. markdown links

Obsidian supports both `[[wikilink]]` and `[text](path)` syntax, and
**defaults to generating wikilinks** when you create a link through its
UI. Portable markdown links still work and render identically inside
Obsidian; wikilinks do not render as links anywhere outside Obsidian
(GitHub shows `[[Note Name]]` as literal bracketed text). That's the
actual decision: wikilinks inside a vault meant to stay inside Obsidian,
plain markdown links in anything that might ever be read outside it
(a note that gets published, copied into a repo, or read by
`mcp__obs-vault__*` tooling that expects portable links).

| Need | Syntax |
|---|---|
| Link to a note | `[[Note Name]]` |
| Link to a note in a folder | `[[Projects/Note Name]]` |
| Link with custom display text | `[[Note Name\|Display Text]]` |
| Link to a heading in the same note | `[[#Heading]]` |
| Link to a heading in another note | `[[Note Name#Heading]]` |
| Link to a nested subheading | `[[Note Name#Heading#Subheading]]` |
| Link to a specific block | `[[Note Name#^block-id]]` |
| Embed (transclude) a whole note or image | `![[Note Name]]` / `![[image.png]]` |

Block references (`^block-id`) are worth using deliberately rather than
letting Obsidian auto-generate one: a hand-chosen `^quote-of-the-day`
stays readable in the link; an auto-generated `^37066d` doesn't tell a
future reader anything about what it points to.

## Callouts — a superset of GitHub's alerts, not a match

Obsidian's callout syntax (`> [!type]`) predates and is richer than
GitHub's five alert types ([github-flavor.md](github-flavor.md)): 13 built-in types —
`note`, `abstract` (alias `summary`/`tldr`), `info`, `todo`, `tip` (alias
`hint`/`important`), `success` (alias `check`/`done`), `question` (alias
`help`/`faq`), `warning` (alias `caution`/`attention`), `failure` (alias
`fail`/`missing`), `danger` (alias `error`), `bug`, `example`, `quote`
(alias `cite`) — plus a custom-title override, folding, and nesting GitHub
alerts don't have:

```markdown
> [!warning]- Collapsed by default, custom title
> Content only visible once expanded.

> [!question] Parent
> > [!todo] Nested one level
```

`+` after the type makes a callout default-expanded-but-foldable; `-`
makes it default-collapsed. Text after the type on the same line replaces
the default title.

**The compatibility direction that matters:** GitHub's five alert
keywords (`note`/`tip`/`important`/`warning`/`caution`) are a subset of
Obsidian's types and render fine in Obsidian too. The reverse isn't
true — an Obsidian-only type like `[!bug]` or `[!example]` renders as a
plain blockquote with the literal text `[!bug]` on GitHub, because GitHub
only recognizes its own five keywords. Write with GitHub's five whenever
the note might ever be read there; use the Obsidian-only types freely for
anything that stays vault-only.

## Properties (frontmatter)

Any YAML key becomes a property, editable through the Properties panel UI
without hand-writing YAML. Three keys are special-cased by Obsidian
itself: `tags` (adds to the tag index and graph view), `aliases`
(alternate names the note is searchable/linkable by), `cssclasses`
(applies a CSS class to the note's rendering, vault-styling only). See
[frontmatter.md](frontmatter.md) for how this schema compares to the other three in active
use across this vault.

## Tags

`#tag` inline, or listed in the `tags:` property. Nested tags use `/`:
`#project/api-gateway`. Prefer the `tags:` property for a note's primary
classification (visible, structured, searchable in the Properties panel)
and inline `#tags` for a passing cross-reference inside the prose itself.
