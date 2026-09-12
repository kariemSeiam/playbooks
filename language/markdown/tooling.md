# Tooling — making the law mechanically enforced

Every other file in this playbook is manual law: read it, then run
[preflight-checklist.md](preflight-checklist.md) by hand per file. That works for the low volume
of files one person writes deliberately, and stops working the moment a
repo has more than a couple of contributors or more than a few dozen
markdown files — nobody re-reads [syntax.md](syntax.md) before every commit.
`markdownlint.config.json` (same folder) turns the mechanical half of
[syntax.md](syntax.md) into something a linter checks in CI, so a fence missing a
language fails a build instead of surviving until someone happens to
notice it.

## Using the config

Copy `markdownlint.config.json` to a repo's root as `.markdownlint.json`
(or `.markdownlint.jsonc` if comments are wanted — `markdownlint-cli2`
accepts either), then run it via [`markdownlint-cli2`](
https://github.com/DavidAnson/markdownlint-cli2), the actively maintained
CLI (not the older `markdownlint-cli`):

```bash
npx markdownlint-cli2 "**/*.md" "#node_modules" "#dist"
```

## What each override encodes, and why it isn't the default

The config starts from `"default": true` (every rule on) and overrides
only where this playbook's own stated rules diverge from the tool's
defaults — each override traces back to a specific line in [syntax.md](syntax.md)
or [voice.md](voice.md), not a personal preference invented here:

<!-- markdownlint-disable MD044 -->
| Rule | Override | Source |
|---|---|---|
| MD003 | `atx` style | [syntax.md](syntax.md): "ATX style, never Setext" |
| MD004 | `dash` bullets | [syntax.md](syntax.md): "one consistent bullet marker" |
| MD013 (line length) | off | Not a rule this playbook states anywhere — leaving it on would invent a constraint and fail every existing file |
| MD024 (duplicate headings) | `siblings_only` | Allows the Keep-a-Changelog pattern (repeated `### Security` under different version headings) that `../github/changelog-and-releases.md`'s worked example and this repo's own `CHANGELOG.md` rely on, while still catching a real collision within the same section |
| MD029 | ordered-list style `one_or_ordered` | [syntax.md](syntax.md) permits **both**, conditionally: all-`1.` "for ordered lists that will be edited over time," but "for a short, stable list, sequential numbers are fine." `one_or_ordered` encodes exactly that — either style, as long as a given list is internally consistent. This config previously said `one`, which was stricter than the rule it cited and flagged 288 correct lines; the config was wrong, not the content |
| MD033 (no inline HTML) | **off** | [syntax.md](syntax.md) and [github-flavor.md](github-flavor.md) both deliberately endorse HTML escape hatches (`<details>`, `<div align>`, `<picture>`) — the default-on behavior would flag every one of them |
| MD041 (must start with H1) | **off** | [frontmatter.md](frontmatter.md) covers files that legitimately start with a YAML block before any heading |
| MD044 (proper names) | a short list (GitHub, npm, MCP, Mermaid, GFM) | Catches "github" → "GitHub" drift. Deliberately excludes "Markdown" — this playbook's own files consistently and correctly use lowercase "markdown" as the common noun for the format, capitalizing only the specific historical Markdown language; adding it to the list would flag dozens of already-correct sentences |
| MD060 (table pipe padding) | **off** | Directly conflicts with [syntax.md](syntax.md)'s own stated position: "pipe alignment doesn't need to be visually perfect in source... don't spend effort padding pipes if content changes often" |
<!-- markdownlint-enable MD044 -->

The MD044/MD060 overrides above weren't decided from reading rule
descriptions — they came from actually running the config against this
playbook's own 12 files and finding it flagged things [syntax.md](syntax.md) already
explicitly permits. Do the same before trusting a config change: run it
against real files, don't just reason about what a rule *should* do.

## `--fix` is not safe to run unsupervised on MD044

Learned by running it, not by reading the docs: `markdownlint-cli2 --fix`
silently rewrote `[github-flavor.md](github-flavor.md)` to
`[GitHub-flavor.md](github-flavor.md)` in ten places across six files —
<!-- markdownlint-disable-next-line MD044 -->
MD044 matched "github" inside a **filename** in link text and
"corrected" it, leaving link text that no longer matches the file it
points to. The link still resolves (the target in parentheses is
untouched), so nothing breaks loudly; it just quietly starts lying.

The rule to carry: `--fix` is safe and genuinely useful for the
whitespace/structure rules (MD022, MD032, MD007, MD012, MD058 — it
cleared 350 real violations here in one pass), and unsafe for the
content rules that require judgment (MD044 especially). Run
`--fix`, then **diff before committing** — specifically grep the diff
for proper-name changes inside link text and filenames.

## A known false-positive, and how to suppress it correctly

MD044 can't distinguish a brand name from a domain string that happens to
<!-- markdownlint-disable-next-line MD044 -->
contain it — "github.com" (correctly lowercase, it's a URL) still matches
against "GitHub" in the proper-names list. Don't remove "GitHub" from the
list over this — that loses the rule's real value everywhere else it's
not a domain name. Suppress the specific line instead:

```markdown
<!-- markdownlint-disable-next-line MD044 -->
See github.com for details.
```

## Prettier and markdownlint aren't the same job — don't let them fight

Prettier reformats markdown (`proseWrap`, list-marker normalization);
markdownlint only reports violations, it doesn't rewrite anything. Run
both, but turn off the markdownlint rules Prettier already owns (list
indentation, some whitespace rules) rather than letting the two disagree
about the same line and produce a lint failure Prettier's own `--write`
just re-introduces. `markdownlint-cli2`'s own docs maintain a
compatibility note for exactly this pairing — check it before adding
Prettier to a repo that already has this config.

## CI wiring

```yaml
# .github/workflows/lint-docs.yml
- run: npx markdownlint-cli2 "**/*.md" "#node_modules"
```

One job, no config beyond pointing at `.markdownlint.json` — the config
file is the actual law; the CI step just makes it non-optional.
