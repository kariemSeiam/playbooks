# Subagent collections ride inside plugins — check what already exists first

Large subagent collections distribute as plugins for exactly the bundling
reason [mechanism.md](mechanism.md) describes — a single marketplace install can carry
hundreds of specialized agent definitions alongside skills and commands.
Before reaching for one: check whether this environment's own existing
custom subagent definitions already cover the role a collection's agent
would fill. A plugin-sourced subagent is worth adopting only for a role
nothing already wired in covers, not as a parallel system or a
replacement for one that already works — adopting a second definition for
a role already covered is drift, the same failure mode [ecosystem.md](../mcp/ecosystem.md)
names for a duplicate MCP server.

## Related

- [mechanism.md](mechanism.md) — how a plugin bundles a subagent collection in the
  first place, and why it doesn't travel across harnesses the way the
  agents inside it conceptually could.
