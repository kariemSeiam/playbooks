# GitHub anatomy — repos, Issues, PRs, releases, security

This covers the layer above git itself: GitHub's own constructs (Issues,
PRs, releases, labels, repo settings, Actions). Each one below has a real
purpose and a real cost — the craft is knowing which a given project has
actually earned the right to use, not defaulting to all of them because
they exist. Most of GitHub's ceremony is genuine overhead below a certain
project size, and a genuine liability if skipped above it.

## Repositories

- **Visibility**: private by default for anything not explicitly meant to
  be public yet. Flipping private→public is effectively one-way in
  practice — forks and clones of a public repo persist even after
  re-privating — so treat it as a real decision, not a toggle to flip
  back later without cost.
- **Description**: worth setting the moment a repo has any real shape.
  Fine to leave empty during early scaffolding.
- **Default branch**: `main`, no reason to deviate absent an existing
  convention that says otherwise.
- **Branch protection rules** (require PR, require status checks, forbid
  direct push): exist to make review and CI mandatory. Correct the moment
  a team has more than one contributor whose work needs a gate before
  landing, or a CI signal that must pass before merge. Actively
  counter-productive for solo trunk-based work (see
  [concurrency-and-branching.md](concurrency-and-branching.md)) — it adds a mandatory round-trip with no
  one on the other end of it.

## Issues

Earns its place the moment there's a backlog worth tracking *across
sessions/time* — "do this later, not now" items that would otherwise only
live in a chat transcript, a `TODO` comment that rots, or someone's memory.
Not worth it for work that completes within a single continuous session
where nothing needs to survive until later.

The concrete trigger for adopting Issues on a project that doesn't use
them yet: the first time something genuinely needs to persist as "not
done yet" past the current session. Once Issues exist, commit footers
reference them (`Fixes #N` auto-closes on merge to default branch,
`Refs #N` links without closing — see [commits.md](commits.md)).

## Pull Requests

Exist to gate merging behind review. For solo trunk-based work, a PR is
pure overhead with no reviewer on the other side of it — commit directly
to the default branch instead. The one case a PR earns its place even
solo: a change large or risky enough that reading the whole diff as one
unit, before it's final, is genuinely more useful than reviewing it
commit-by-commit as it lands. That's a per-change judgment call, not a
standing policy.

If a PR is used: the title should read like a good commit header (type +
what, imperative, no trailing period); the body should cover what changed,
why, and a test plan if there's anything a reviewer needs to verify
manually rather than just read. Multi-line PR bodies should go through a
heredoc when created via CLI tooling, never inline — inline multi-line
content is where shell-quoting bugs live.

## Releases and tags

Earn their place the moment either: (a) something outside the repo
consumes it at a pinned version, or (b) there's value in a changelog/
version history independent of the raw commit log. Semantic versioning
(`vMAJOR.MINOR.PATCH`) is the default convention once this starts —
`MAJOR` for breaking changes (this is exactly what the `BREAKING CHANGE:`
commit footer trailer exists to drive), `MINOR` for new backward-compatible
capability, `PATCH` for fixes only. Tagging without any consumer and
without any changelog need is ceremony without a payoff — skip it until
one of the two conditions is real.

## Labels and milestones

Only worth the setup cost alongside Issues, and only once there's enough
issue volume that grouping/filtering actually helps navigate them. A
handful of issues doesn't need a label taxonomy; dozens or hundreds might.

## Security features — cheap, no real downside, worth enabling early

Once any repo exists on GitHub — private or not — these cost essentially
nothing and catch real mistakes:

- **Secret scanning** — flags an accidentally committed API key/token.
  Complements, never replaces, the discipline of never committing
  `.env`/`*.key`/`*.pem`-style files in the first place (see
  [preflight-checklist.md](preflight-checklist.md)) — it's a second layer, not the first.
- **Dependabot alerts** — flags known-vulnerable dependencies. Harmless to
  leave on even for a project with few or no dependencies yet.

These are the rare GitHub features that are correct to enable by default
regardless of project size, unlike branch protection/required PRs/CI gates
above, which are correct only once the conditions that justify them exist.

## GitHub Actions / CI

Earns its place once a project has a test suite (or equivalent automated
check) whose pass/fail signal is worth gating on automatically, and there's
value in that signal running somewhere independent of wherever development
happens locally. Not worth the setup for a project with no test suite yet,
or for a workflow where local verification already produces the same
signal a CI run would (a build/typecheck/test command run inline as part
of the development loop already *is* that signal, just running locally
instead of on a hosted runner) — adding CI on top of that duplicates the
check without adding new information, until the project actually needs the
independence (e.g. verifying a change works outside the exact local
environment it was authored in).

## The one hard rule, regardless of project size or GitHub feature adoption

Never enter credentials, tokens, or secrets into any GitHub surface (repo
settings, issue text, PR description, commit content, release notes) as
plain text. If a secret needs to exist for a project, it belongs in an
untracked, gitignored file — never in anything that becomes part of git
history or a GitHub-hosted text field, both of which are effectively
permanent even after a later "removal."
