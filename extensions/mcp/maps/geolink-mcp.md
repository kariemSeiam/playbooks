# Map: a location-intelligence MCP server, studied for its design

A map, not law — this documents one real, external MCP server
(`geolink-mcp`, an npm-published GeoLink integration) as a worked
example of the principles in [authoring-a-server.md](../authoring-a-server.md) and the
Skill/MCP pairing in [mechanism.md](../mechanism.md). Read those for the timeless
version; read this for what a mature implementation of them actually
looks like end to end.

## The shape: agent-shaped answers first, endpoints second

Most geocoding MCP servers are thin 1:1 wrappers — one tool per upstream
endpoint, raw JSON dumped into context. This one is built the other way
around. Its seven tools cover geocode, reverse-geocode, search, directions,
a distance matrix, and two *composite* tools that don't map to any single
upstream endpoint at all:

- **A ranked-nearest tool** that routes every candidate through the
  matrix endpoint and re-ranks by real road travel time, instead of
  answering "nearest" with straight-line distance in a city full of
  rivers, one-ways, and bridges.
- **An area-sweep tool** that tiles a whole region with a query grid
  (de-duplicated across cells, grouped by district), because a single
  search call only ever returns one page from one center point — and a
  `dry_run` mode that returns the exact call count before spending it, so
  "sweep this whole city" never produces a surprise bill.

## The pairing: server for capability, Skill for judgment

The server's raw tool calls don't teach an agent when a returned count is
actually complete, when a name collision resolved to the wrong place, or
when to page deeper versus trust the first result. This implementation
pairs the server with a companion Skill covering exactly that judgment
layer — the concrete instance of [mechanism.md](../mechanism.md)'s general rule that
an MCP server supplies ability and a Skill supplies the discipline for
using it well.

## Three things worth carrying forward

- **Knowledge that reaches clients with no filesystem, from one source.**
  The Skill's own reference material is also served as MCP Resources,
  generated from the identical files a filesystem-based client would
  read directly — with a test asserting the served text is byte-identical
  to the file on disk. One source, two delivery paths, verified never to
  drift apart. This is what closes the gap [mechanism.md](../mechanism.md)'s pairing
  otherwise leaves open: a pure chat harness with no filesystem still
  gets the discipline layer, not just the raw tool calls.
- **Errors that teach, not errors that just fail.** Every failure returns
  in-band as `Error (<kind>): <what happened>` followed by
  `Next step: <the exact parameter change that would succeed>`. A
  guard-rail error — a request over a hard cap — names the smallest
  change that would pass, so the calling agent self-corrects and retries
  right on the first try instead of retrying blind.
- **Claims kept re-verifiable, not stated once and trusted forever.** A
  small script re-measures documented numbers (grid math, latency,
  response variance) against the live system and flags drift, alongside
  a ledger recording what was claimed and how it was last checked. A
  reference whose numbers rot is worse than none, because the rot is
  invisible — this is the concrete answer to that failure mode.

## What's worth questioning, not just copying

The header image is pulled via a hardcoded `raw.githubusercontent.com`
URL pinned to a branch name — works today, breaks silently the day that
path or branch changes, and nothing in the test suite would catch it the
way the Resources byte-identity test catches everything else. The one
place this implementation's own "nothing that rots invisibly" standard
doesn't quite apply to itself.

## Related

- [authoring-a-server.md](../authoring-a-server.md) — the general principles this map is one
  worked instance of.
- [mechanism.md](../mechanism.md) — the Skill/MCP-server pairing this map's second
  section demonstrates concretely.
