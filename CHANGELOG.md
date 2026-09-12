# Changelog

All notable changes to this project are documented here. Format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versioning
follows [Semantic Versioning](https://semver.org/) once a `MAJOR` version
is warranted (see `github/platform.md`).

## [Unreleased]

### Added

- A copy-paste onboarding prompt in the README: one block a reader drops
  into whatever agent they already run, which then detects its own
  harness, clones the vault, and wires it into that harness's global
  instructions file — merging, never overwriting.
- `extensions/onboarding-prompt.md` — the standing law behind that block:
  the five things a paste-install prompt has to control end to end, since
  the moment it's pasted the publisher has no steering left.
- CI: `.github/workflows/lint-docs.yml` runs `markdownlint-cli2` on every
  push and PR, wired exactly as `language/markdown/tooling.md` already
  prescribed but had never actually been applied to this repo.
- `.markdownlint.json` at the repo root, per that same note's own
  instructions.

### Changed

- `MD029` config relaxed from `one` to `one_or_ordered`. The config was
  stricter than the `syntax.md` rule it claimed to encode — `syntax.md`
  permits sequential numbering "for a short, stable list" — and was
  flagging 288 correct lines. The config was wrong, not the content.

### Fixed

- 410 real lint violations across the vault: blank lines around lists,
  headings and tables, list indentation, 40 unlabelled code fences in
  `finance/`, and emphasis used where a real heading belonged.
- A line in `github/platform.md` where `` `Refs #N` `` had been wrapped
  across a line break, leaving `#N` at line start and parsing as a
  stray H1.
- `language/markdown/tooling.md` gained a section on `--fix` being unsafe
  for MD044 — it silently rewrote ten filename link texts to
  `[GitHub-flavor.md](github-flavor.md)`, which resolves but no longer
  matches the file it names. Found by running it, not by reading docs.

## [0.2.0] - 2026-09-12

### Added

- `seo/` as its own top-level pillar: `fundamentals.md` (the three
  classic SEO pillars), `generative-engine-optimization.md` (GEO/AEO —
  being cited inside an LLM's answer), `developer-platform-discoverability.md`
  (GitHub/npm-specific signals).
- `github/discoverability-checklist.md` — the procedural checklist for
  making a repo public, sibling to `preflight-checklist.md`.
- `github/changelog-and-releases.md` — this file's own format, made
  canonical law instead of an assumed convention.

### Fixed

- A cross-reference in `language/markdown/tooling.md` that pointed at a
  "worked example" in `github-flavor.md` and at "this vault's own
  `CHANGELOG.md`" — neither existed yet. Both now do.
- A stale reference to a third agent harness that isn't actually part of
  this repo's scope, and an absolute local filesystem path that had no
  business in a public repo's operating instructions — both left over
  from before this repo was split out from a private vault.

## [0.1.0] - 2026-09-12

### Added

- Initial public release: 139 notes across 11 folders. Procedural law
  (`github/`, `language/markdown/`, `extensions/`) and declarative field
  notes (`software-engineering/` plus 7 business domains), one fixed
  7-part shape per declarative note.
- `extensions/` — Skills, MCP servers, and plugins, with real external
  implementations studied under `extensions/*/maps/`, kept structurally
  separate from the law itself.
- `CLAUDE.md`, symlinked as `AGENTS.md`, so Claude Code and OpenCode read
  identical operating law with nothing to keep in sync by hand.
- MIT license.

[Unreleased]: https://github.com/kariemSeiam/playbooks/compare/v0.2.0...HEAD
[0.2.0]: https://github.com/kariemSeiam/playbooks/compare/v0.1.0...v0.2.0
[0.1.0]: https://github.com/kariemSeiam/playbooks/releases/tag/v0.1.0
