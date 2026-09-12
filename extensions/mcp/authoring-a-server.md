# Authoring an MCP server well

[mechanism.md](mechanism.md) covers what an MCP server is and when a gap needs one;
this note is about building one that's actually good — three principles
worth holding as law, each with a worked instance in `maps/` for what it
looks like in practice.

## Knowledge should reach clients with no filesystem, from one source

A Skill reaches an agent through its filesystem — no filesystem, no
Skill. An MCP server doesn't have that limit: it can serve the same
judgment-layer knowledge a Skill would carry — which tool to use when,
the failure modes, the worked compositions — as MCP **Resources**,
generated from the identical source a filesystem-based client would read
directly, with a test asserting the served text is byte-identical to the
source. One source, two delivery paths, verified never to drift apart.
This closes a real gap in the Skill/MCP pairing ([mechanism.md](mechanism.md)): a pure
chat harness with no filesystem still needs the discipline layer, not
just the raw tool calls, and Resources are how it gets it without
anything to install.

## Errors that teach, not errors that just fail

An MCP tool's error isn't a stack trace or a bare failure flag — the
useful shape names what happened and what would fix it:
`Error (<kind>): <what happened>` followed by
`Next step: <the exact parameter change that would succeed>`. A
guard-rail error — a request over a hard cap, say — that names the
smallest change that would actually pass lets the calling agent
self-correct and retry correctly on the first try, instead of retrying
blind or giving up. This is a different context than
[rest-api-design.md](../../software-engineering/rest-api-design.md)'s RFC 9457 Problem
Details format (that's HTTP status-code semantics; a tool call has
neither) but the same underlying discipline: an error is a second chance
to be useful, not just a report that something failed.

## Claims should stay re-verifiable, not just documented once

A static number in a reference doc — call volume, latency, a coverage
figure — rots the moment the underlying system changes, and the rot is
invisible: nothing fails, the number just quietly stops being true. The
stronger pattern is a small script that re-measures the number against
the live system and flags drift, paired with a ledger recording what was
claimed and how it was last verified. Anything in this vault that
documents a live system's current state — not just timeless mechanism —
is exposed to this same rot and should carry the same discipline where
it's practical to add.

## Related

- [mechanism.md](mechanism.md) — the Skill/MCP-server pairing the first principle
  above extends to filesystem-less clients.
- **`maps/`** — real, external implementations studied for how these
  principles actually play out, not just stated in the abstract.
