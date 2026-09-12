# Changelog and releases — the human-facing layer above the commit log

[platform.md](platform.md)'s "Releases and tags" section states *when* tagging earns
its place; this note is the *how*, for the two things that earn their
place together: a `CHANGELOG.md` a person can skim without reading every
commit, and the semantic-version tags that give its entries something
real to be named after.

## Why a changelog isn't just the commit log reformatted

A commit message ([commits.md](commits.md)) is written for someone reading `git log`
one commit at a time, in the order things actually happened, including
every false start and fixup. A changelog entry is written for someone
who wants to know what's different since the version they last used —
grouped by *kind* of change, not chronological order, and silent about
anything that doesn't affect a consumer (an internal refactor, a typo
fix in a comment) even if it was its own commit. Conflating the two
produces a changelog that's just `git log --oneline` with extra
formatting — technically present, not actually useful to the reader it's
for.

## The Keep a Changelog format

[keepachangelog.com](https://keepachangelog.com)'s convention, adopted
here rather than invented: one `##` heading per released version
(newest first), each broken into a fixed set of `###` subheadings, used
only when that version actually has entries of that kind:

- **Added** — new capability.
- **Changed** — behavior that existed before, now different.
- **Deprecated** — soon-to-be-removed, still working for now.
- **Removed** — actually gone.
- **Fixed** — a bug corrected.
- **Security** — a vulnerability closed.

An `## [Unreleased]` section at the top collects entries as they land,
between releases — this is what makes MD024 (duplicate-heading
detection) need its `siblings_only` override
([tooling.md](../language/markdown/tooling.md)): `### Security` genuinely repeats
under every version heading that has one, and that's correct, not a
collision.

```markdown
## [Unreleased]

### Added
- New capability landing on `main`, not yet cut into a release.

## [0.2.0] - 2026-09-12

### Added
- `seo/` as a new pillar: SEO fundamentals, GEO/AEO, developer-platform
  discoverability.
- `github/discoverability-checklist.md`.

### Fixed
- A cross-reference in `tooling.md` that pointed at a worked example
  that was never actually written.
```

## What actually generates an entry

Not every commit — only ones whose effect a consumer of the repo (not a
contributor reading its history) would care about. Map from
[commits.md](commits.md)'s type taxonomy: `feat` → **Added**, a behavior-changing
`fix` → **Fixed**, `BREAKING CHANGE:` in a commit footer → **Changed**
(called out explicitly, not buried in prose), a `refactor`/`chore`/`docs`
commit → usually nothing, unless the docs change is itself
user-facing (a corrected public-facing claim, say). Write the entry at
the same time as the commit it corresponds to, in the `[Unreleased]`
section — reconstructing a changelog from history after the fact, the
way this repo's own [CHANGELOG.md](../CHANGELOG.md) had to be for its first two versions,
is strictly worse: detail gets lost, and "what a consumer would care
about" is a harder judgment call in hindsight than in the moment.

## Cutting a release

1. Move everything under `[Unreleased]` into a new version heading, dated
   `YYYY-MM-DD`.
2. Decide the version bump per [platform.md](platform.md)'s semver rule: `MAJOR` for
   anything under **Changed** that breaks an existing consumer, `MINOR`
   if there's anything under **Added**, `PATCH` if the release is
   **Fixed**/**Security** only.
3. Tag the commit (`git tag -a v0.2.0 -m "..."`, annotated not
   lightweight — the message is what `git show` on the tag actually
   displays) and push the tag (`git push --tag`) — same explicit
   go-ahead discipline as any push, per [preflight-checklist.md](preflight-checklist.md) step 7.
4. Leave a fresh empty `[Unreleased]` section at the top for what comes
   next.

## Related

- [platform.md](platform.md) — when tagging and a changelog earn their place at
  all; this note assumes that bar is already cleared.
- [commits.md](commits.md) — the type taxonomy a changelog entry's category maps
  from.
- [tooling.md](../language/markdown/tooling.md) — the MD024 override this
  format's repeated `### Security` headings require.
