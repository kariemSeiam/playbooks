# The external MCP landscape, for when a gap needs a server that doesn't exist yet

Registry and marketplace aren't the same layer. A **registry** is the
canonical, machine-readable index — the community MCP Registry is this:
publishing there means proving ownership of a name and shipping a
`server.json` other tools can read. A **marketplace** is the human-facing
discovery layer built on top: search, categories, ratings, one-click
install, sometimes hosting.

Three marketplaces, shaped differently enough that a thin search on one
isn't a search of the whole ecosystem:

- **Smithery** (smithery.ai) — ~7K servers, the only one of the three
  that can run a server for you (hosted remote deployment) rather than
  just pointing at where to install one.
- **Glama** (glama.ai) — the largest crawl, ~37K servers tracked, with a
  separate tier for owner-claimed (verified) entries versus
  auto-discovered ones — verification status matters more here than raw
  count.
- **PulseMCP** — ranks by estimated weekly visitor count, the only one of
  the three where standing is measured by actual usage rather than
  install count or stars.

Because MCP is an open, vendor-neutral protocol — not a Claude Code
convention — a server found through any of these three runs the same way
regardless of which harness connects to it. That's the one piece of this
whole `extensions/` category that's cross-harness by protocol design, not
just by convention two implementations happened to agree on the way
Skills are.

## Before adding a new one

The same discipline as adding a Skill, with higher stakes because a
server is running code with real tool-call access, not inert text:

1. Name the actual capability gap first — if the honest answer is
   "the model doesn't know how," that's a Skill, not a server.
2. Check whether an existing connection already covers it before adding a
   new one — a second server for the same capability is drift, not
   redundancy.
3. Treat a newly connected server's first real write the way any new,
   unverified tool's first real action gets treated: confirm before
   trusting it with something that has a real-world consequence.

## Related

- [mechanism.md](mechanism.md) — confirms it's genuinely a capability gap, not a
  knowledge gap, before searching for a server at all.
- [authoring-a-server.md](authoring-a-server.md) — once the answer is "build one," the
  principles to build it against.
