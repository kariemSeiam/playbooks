# What a Skill actually is, and where it lives

## The mechanism

A Skill is a `SKILL.md` file with two layers: YAML frontmatter (`name`,
`description`) that the harness keeps loaded for every session at near-
zero cost, and a markdown body that only loads once the frontmatter
signals relevance to whatever's actually being asked. This is
[for-agents.md](../../language/markdown/for-agents.md)'s cover/chapter split, just enforced by
the harness itself instead of by an agent's own discipline about which
files to open — the frontmatter *is* the cover, and nothing past it gets
read until the description earns that.

That's the entire mechanical difference from a plain playbook note: a
note in `github/` or `finance/` only gets read if the agent remembers to
check that folder for the task at hand. A Skill's description gets
checked against every task, automatically, whether or not the folder
crosses its mind. The cost of that reliability is that the description
has to be written well enough to fire on the right tasks and stay silent
on everything else — a bad description either never triggers (dead
weight) or triggers on the wrong things (noise, the same failure mode as
an over-broad regex).

## Not a Claude Code convention wearing a generic name

`SKILL.md` follows the open Anthropic Agent Skills Spec, and OpenCode
implements the same spec independently, reading skills from the identical
`~/.claude/skills/` directory (plus its own `~/.agents/skills/`). A
symlink from any other agent's own skills directory into one of those
shared paths works exactly the way a symlink into any shared resource
does: one file, live across every harness that reads that path, no copy
to keep in sync. A Skill installed once, globally, is closer to a fact
about a whole agent setup than a fact about any one harness.

## Where a Skill lives

Two scopes, and — because more than one harness reads the same
convention — more than one path per scope in practice:

| Scope | Claude Code reads | OpenCode also reads | Applies to |
|---|---|---|---|
| Project | `<repo>/.claude/skills/` | `<repo>/.opencode/` | That repo only — committed, shared with anyone working in it |
| Global | `~/.claude/skills/` | `~/.config/opencode/skills/`, `~/.agents/skills/` | Every session, every repo, regardless of which project is open, in either harness |

Standing law meant to hold "whenever it's relevant, on anything touched"
is global by construction. A Skill scoped to one repo is closer to that
project's own `CLAUDE.md` — real, but local to it. And because
`~/.agents/skills/` is a shared global path both harnesses already check,
installing there once (or symlinking a skill from elsewhere into it) is
the version of "global" that actually means *every agent in this
environment*, not just one harness.

## Related

- [ecosystem.md](ecosystem.md) — the open registries to search before building a new
  one from scratch.
- [promotion-and-authoring.md](promotion-and-authoring.md) — when a playbook note here earns
  promotion into a Skill, and how this vault writes one.
