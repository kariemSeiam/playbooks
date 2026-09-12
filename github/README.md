# git/GitHub playbook — read before any git or GitHub action

This is standing knowledge, not project notes and not a memory of one
conversation. It is meant to be as true and as useful for a repo that
doesn't exist yet as for one that's a decade old. Consult it BEFORE
running any `git` command with side effects (add/commit/push/branch/tag/
remote) or any GitHub action (repo/issue/PR/release), the same way a
skill gets read before it's followed — not skimmed once and approximated
from memory thereafter.

## Files in this playbook

- [commits.md](commits.md) — what a commit actually is: anatomy, the type
  taxonomy, and the reasoning (not just the etiquette) behind message
  quality. Read before writing any commit message that isn't a trivial
  one-liner.
- [concurrency-and-branching.md](concurrency-and-branching.md) — the branching-model decision
  framework (trunk-based vs. release branches vs. Git Flow — when each is
  actually correct, not "always use X"), and the isolation discipline
  required the moment more than one process — human or agent — can touch
  the same working tree in overlapping time.
- [platform.md](platform.md) — GitHub's own layer on top of git: repos, Issues, PRs,
  releases, labels, security features, CI — what each is *for*, and the
  maturity signal that tells you a project has actually earned the right
  to use it (most of GitHub's ceremony is overhead below a certain size,
  and a real liability above it if skipped).
- [preflight-checklist.md](preflight-checklist.md) — the concrete sequence to run, every
  time, before any git/GitHub action with real effect. The other three
  files are the reasoning; this one is the thing to actually execute.
- [discoverability-checklist.md](discoverability-checklist.md) — the separate checklist for whether a
  repo will actually be found once it's public: description, topics,
  README, social preview, the AI-crawler layer when it's earned. A
  sibling to the preflight checklist, not a replacement — that one is
  about the safety of the action, this one is about the result.

## How to use a project-specific override

Any given project may have its own git conventions that differ from this
playbook's defaults (a `CONTRIBUTING.md`, a note in its own `CLAUDE.md` or
agent-memory file, an explicit standing instruction from the person who
owns it). **A project's own stated convention always wins over this
playbook's default.** This playbook is the fallback for when nothing more
specific has been said — never a mandate that overrides an explicit local
rule. Check for one before assuming the defaults here apply.

## Why this exists

Because acting on git/GitHub without first having internalized *why* the
conventions are what they are produces technically-valid-looking commits
that are still low quality — vague, non-atomic, undocumented in the one
way that would have mattered later. Knowing the mechanics (`git commit
-m`) isn't the same as knowing the craft (what that message should say and
why). This playbook is the difference between the two, made explicit and
durable instead of re-derived under time pressure every time.
