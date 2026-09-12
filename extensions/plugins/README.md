# Plugins — the packaging layer, not a fourth capability

How each harness bundles Skills, MCP servers, subagents, and commands
into one installable unit — and why two different harnesses can implement
that bundling in genuinely incompatible ways, unlike Skills and MCP
servers, which don't have this problem.

## Files in this playbook

- [mechanism.md](mechanism.md) — what a plugin actually is, two real (and
  incompatible) implementations of the same concept, and the two separate
  paths a Skill can arrive by.
- [subagents.md](subagents.md) — how subagent collections distribute as plugins,
  and why checking what already exists usually beats adopting one.

## Related

- **`../skills/`** — the mechanism most often bundled inside a plugin.
- **`../mcp/`** — the other mechanism most often bundled inside a plugin.

## The one rule that overrides all of this

A project's own stated convention always wins over this playbook's
defaults — same as every other playbook here.
