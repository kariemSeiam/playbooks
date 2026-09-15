# Software engineering — declarative field notes

Different job than `github/` or `language/` — those two are procedural,
standing law about how I act. This is declarative: facts and frameworks
about building software well, a body of knowledge independent of any
instruction about my own behavior. Seeded first because it's the field
most directly underneath the actual work this vault supports (multi-brand
Astro/TS work, real backend services in Bun/Hono/MySQL and
Node/Express/Mongo, and an AI agent's own orchestrator architecture).

## The note shape (every file here follows this)

1. **Definition** — what it is, in enough historical/practical context to
   know why it exists, not just a dictionary line.
2. **When to use** — concrete trigger situations, not abstract conditions.
3. **How it works** — the actual mechanism, in full, not a summary.
4. **Example** — one worked, concrete scenario.
5. **Applying it for a client** — practical guidance for a real
   engagement, not restated theory.
6. **Watch-outs** — specific failure modes and misconceptions.
7. **Related** — links to the other notes that genuinely connect, with a
   one-line reason each.

A note that can't fill section 5 with something a consultant would
actually say to a client is either too abstract to be useful yet, or
belongs in a procedural playbook (`github/`, `language/`) instead —
that's the test for which side of the split it's on.

## Notes

- [software-architecture-principles.md](software-architecture-principles.md) — separation of concerns,
  coupling/cohesion, single responsibility, stable-contract encapsulation.
  The principles behind why a well-run multi-brand token architecture is
  shaped the way it is, named explicitly.
- [rest-api-design.md](rest-api-design.md) — resource modeling, HTTP method semantics,
  RFC 9457 error format, versioning strategy, pagination, rate limiting.
  Directly applicable to any real backend API you're building.
- [ai-agent-architecture-patterns.md](ai-agent-architecture-patterns.md) — ReAct, tool use, planning,
  reflection, multi-agent orchestration, RAG, human-in-the-loop. The
  patterns a real subagent/orchestrator system would be built from.
- [reverse-tunnel-self-hosting.md](reverse-tunnel-self-hosting.md) — exposing a
  CGNAT/no-static-IP device as a public HTTPS API via an outbound reverse
  SSH tunnel + VPS reverse proxy, and the fail2ban-collateral-ban,
  jail-precedence, and Toybox-vs-GNU pitfalls that actually bite in
  production.

Each note stands alone — read the one relevant to the task, not the whole
folder start to end. New fields (beyond software engineering) get added
here the day they have a first real, researched note — not before.
