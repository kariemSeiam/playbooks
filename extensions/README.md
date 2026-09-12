# Extensions — standing law for what this operator's agents install to extend themselves

Not scoped to Claude Code specifically, even though that's the harness
reading this file right now. Real environments run more than one agent —
Claude Code and [OpenCode](https://opencode.ai) both feature in this
one — and some of what extends one extends all of them for free, because
the underlying formats are open rather than harness-proprietary. This folder
is about the things this operator installs to extend agent capability in
general: Skills, MCP servers, and the packaging/bundling layer each
harness wraps around them. Procedural, the same job as `github/`: read
before touching agent configuration, not after.

Deliberately not called `harness/`: the harness — whichever one is
running — only handles the mechanical half of a Skill: scanning for
`SKILL.md` files and keeping their frontmatter loaded. Whether the body
ever gets read is the model's judgment call, not something the harness
enforces the way a hook does. This folder is about that
judgment-consulted, install-to-extend layer — not the harness's own
deterministic-execution layer, which doesn't live here and may earn its
own playbook later.

## Subfolders

Each mechanism gets its own folder, not a single flat file — the same
shape `language/` uses for `markdown/`: a short [README.md](README.md) index, the
substance split across focused files underneath it.

- **`skills/`** — what a Skill actually is mechanically, why it's already
  cross-harness in practice (not just in theory), the open ecosystem
  around it (skills.sh, ClawHub, Hermes), the rule for when a playbook
  note earns real Skill status, and the authoring convention this vault
  uses when it builds one.
- **`mcp/`** — the other real capability layer: what makes an MCP server a
  fundamentally different kind of extension than a Skill (new tool-calls,
  not new instructions), how to build one well, and the registry/
  marketplace landscape for when a new capability gap needs a server that
  doesn't exist yet.
- **`plugins/`** — the packaging layer, not a fourth capability: how
  Claude Code's plugin system and OpenCode's plugin system both bundle
  Skills/MCP/subagents together, why they're genuinely different
  mechanisms under the same name, and why checking what's already wired
  in usually beats adopting a plugin-sourced subagent collection.

## Files in this folder

- [onboarding-prompt.md](onboarding-prompt.md) — the publisher's side of all of this:
  writing install instructions for an executor that can think. The dial
  between delegating environment judgment and constraining consequences,
  the five boundaries that fall out of it, this repo's own block read
  line by line, and an honest list of what's still wrong with it.

## Why Skills and MCP travel across harnesses and plugins mostly don't

Not every mechanism in this folder generalizes the same way, and that
distinction is the actual organizing principle here, not an accident of
file count:

- A **Skill** (`SKILL.md`) follows the open Anthropic Agent Skills Spec —
  OpenCode reads it from the identical `~/.claude/skills/` directory
  Claude Code does, plus its own `~/.agents/skills/`. One install, two
  harnesses, no translation needed.
- An **MCP server** speaks the Model Context Protocol, an open standard
  with no single owning client — any MCP-compatible harness can point at
  the same running server.
- A **plugin**, by contrast, is each harness's own bundling convention —
  Claude Code's is a marketplace-distributed unit; OpenCode's is
  TypeScript functions returning configuration. Genuinely different
  mechanisms that happen to share a name; a plugin built for one doesn't
  install into the other.

## Related

- **[for-agents.md](../language/markdown/for-agents.md)** — the tiered-loading theory
  (cover/chapter/appendix) that a Skill's frontmatter/body split is one
  concrete implementation of. Read that for the *why*; read this folder
  for the *what*, specific to this operator's extensions.
- **[ai-agent-architecture-patterns.md](../software-engineering/ai-agent-architecture-patterns.md)** — a
  different question: how to architect an agent *system* for a client.
  This folder is about the tooling this operator's own agents run on, not
  a pattern catalog for building one from scratch.

## The one rule that overrides all of this

A project's own stated convention always wins over this playbook's
defaults — same as every other playbook here.
