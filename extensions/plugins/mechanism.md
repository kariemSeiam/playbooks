# What a plugin actually is, and why it isn't portable the way Skills and MCP servers are

Not a peer to Skills and MCP servers — a plugin is the distribution
wrapper that bundles some combination of them (skills, subagents, slash
commands, hooks, MCP servers, LSP servers) into one installable,
versioned unit. "Skill or plugin?" is a category error the same shape as
"chapter or book?" — a plugin is how a bundle of the other mechanisms
ships and updates together, not an alternative to any single one of them.
A docs-lookup MCP server bundled together with a browser-automation MCP
server inside one plugin is the concrete case: both are MCP servers, both
arrived through one install, neither was connected standalone.

## Two real implementations of "plugin," not one convention

The name is shared; the mechanism underneath isn't, and expecting one
harness's plugin to work in the other is the mistake this section exists
to prevent:

- **Claude Code** — a marketplace-distributed bundle. `/plugin` browses
  the official Anthropic marketplace (pre-configured, 200+ plugins);
  `/plugin marketplace add <owner>/<repo>` adds a third-party one first;
  `/plugin install <name>@<marketplace>` installs from either. The unit
  is declarative — a bundle of files the harness reads, not code it runs.
- **OpenCode** — plugins are TypeScript functions that return
  configuration for agents, tools, hooks, and other features. The unit is
  executable — code, not a declared bundle.

A collection built for one doesn't install into the other. Skills and MCP
servers travel across both harnesses because they're open, standalone
formats (see [../skills/mechanism.md](../skills/mechanism.md) and
[../mcp/mechanism.md](../mcp/mechanism.md)); a plugin is each harness's own
answer to "how do I ship several of these together," and those answers
aren't compatible with each other.

## The two paths to the same Skill — worth knowing when something doesn't update

A Skill can land on disk two genuinely different ways: bundled inside a
plugin (Claude Code's native `/plugin` mechanism, versioned with
everything else in that plugin) or installed bare through the skills.sh
CLI (`npx skills add`, nothing to do with the plugin system at all).
`find-skills` arrived the second way. Neither path is more correct than
the other, but they don't share an update mechanism: `npx skills update`
won't touch anything a plugin installed, and `/plugin update` won't touch
anything skills.sh installed. Knowing which path a given skill came
through is the first thing to check when an expected update doesn't take.

## Related

- [subagents.md](subagents.md) — the other thing a plugin commonly bundles, and why
  most of that layer is already covered here.
