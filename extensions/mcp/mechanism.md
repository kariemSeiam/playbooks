# What makes an MCP server a different kind of extension than a Skill

A Skill is markdown the model reads and may choose to apply — pure
instruction, no new ability. An MCP server is running code that hands the
model actual new tool calls: read a live database, hit a real API,
control a browser, send a message. The question that actually decides
which mechanism a gap needs: does closing it mean *telling the model
how*, or does it mean *giving the model something it couldn't do at all
before*? No Skill fixes "the model can't check today's delivery backlog"
if nothing can reach that data — that's an MCP-server gap, not a
knowledge gap, and no amount of well-written instruction closes it.

## The two compose: server for capability, Skill for judgment

A companion Skill doesn't replace the MCP server it's paired with — it's
the judgment layer on top of the server's raw tool calls, covering
exactly what those calls can't: when a returned count is actually
complete versus just the first page, when a search matched the wrong
entity, when to trust a result versus dig deeper. A database-query server
paired with a query-optimization Skill is the same shape: the server
supplies the capability, the Skill supplies the discipline for using it
well. That pairing is the model worth reusing whenever a new server earns
real standing law, not just a tool description — `maps/` has a fully
worked instance of exactly this.

## Related

- [promotion-and-authoring.md](../skills/promotion-and-authoring.md) — the same authoring
  discipline applies when a server's judgment layer earns a Skill of its
  own.
- **`maps/`** — a real implementation of this pairing, studied end to end.
