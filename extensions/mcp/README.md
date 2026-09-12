# MCP servers — the capability layer, not the knowledge layer

What makes an MCP (Model Context Protocol) server a fundamentally
different extension than a Skill, how to build one well, and the
external registry/marketplace landscape for when a new capability gap
needs a server that doesn't exist yet.

## Files in this playbook

- [mechanism.md](mechanism.md) — the real distinction from a Skill (new tool-calls
  vs. new instructions), and the pairing model: server for capability,
  Skill for judgment.
- [authoring-a-server.md](authoring-a-server.md) — building one well: knowledge reaching
  filesystem-less clients through Resources, errors that teach instead of
  just failing, claims kept re-verifiable instead of static.
- [ecosystem.md](ecosystem.md) — registry vs. marketplace, the three worth knowing
  (Smithery, Glama, PulseMCP), and the checklist before adding a new one.
- **`maps/`** — real, external implementations studied for how the
  principles above actually play out. Law lives in the files above; a map
  is one worked instance, not a second copy of the law.

## Related

- **`../skills/`** — the knowledge-layer counterpart; the pairing
  [mechanism.md](mechanism.md) describes.
- **`../plugins/`** — how a server can arrive bundled instead of connected
  standalone.

## The one rule that overrides all of this

A project's own stated convention always wins over this playbook's
defaults — same as every other playbook here.
