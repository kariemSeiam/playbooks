---
domain: people-org
concept: Team Topologies
source: research — Matthew Skelton & Manuel Pais, "Team Topologies" (2019)
tags: [teams, topology, platform, cognitive-load, interaction-modes]
---

# Team Topologies

Team Topologies, from Matthew Skelton and Manuel Pais's 2019 book of the same name, gives an organization exactly four team types and three (plus one) interaction modes, and argues that most organizational design problems in software companies are really **cognitive load** problems in disguise — a team asked to hold too much context in its collective head (too many services, too many domains, too many hand-offs) will underperform regardless of talent or process. Where the Spotify Model describes *what* autonomous teams look like, Team Topologies is more prescriptive about *which* team should own *what*, and exactly *how* two teams should interact given their types — making it a faster diagnostic for a consultant walking into an existing org and asking "why do these two teams keep colliding." It's newer than OKRs, RACI, or the Star Model but has been adopted unusually fast across software organizations since 2019 — **emerging-but-credible**, with a large and still-growing base of practitioner case studies.

## When to use

- Two or more teams are frequently blocked on each other, with unclear or informally negotiated hand-offs that shift depending on who's asking.
- A platform or infrastructure team exists but nobody can articulate whether it's meant to be self-service or a request queue — and in practice it behaves like the latter.
- Diagnosing whether a struggling team's real problem is skill, or simply too much cognitive load — too many unrelated systems or domains for one team to hold well.
- A client wants to introduce a "platform team" or "enabling team" concept but has no vocabulary yet for how it should interact with the teams it supports.
- Following on from a Spotify-Model-style reorg that produced named squads but persistent cross-team friction — Team Topologies gives sharper interaction-mode vocabulary to diagnose exactly where the friction lives.

## How it works

### The core constraint: cognitive load

Skelton and Pais's foundational claim is that team size and scope must fit within what the team can actually hold in their heads — the number of domains, services, and technologies a team is responsible for has a real ceiling, and past that ceiling, quality and speed both degrade regardless of headcount added. Three kinds of cognitive load: **intrinsic** (inherent difficulty of the domain itself, e.g., a genuinely hard algorithm), **extraneous** (unnecessary friction from bad tooling, unclear processes, manual hand-offs), and **germane** (the load of learning and improving, worth spending capacity on). Good team design reduces extraneous load aggressively and protects a team's remaining capacity for intrinsic and germane load.

### Four team types

| Team type | Purpose | Default? |
|---|---|---|
| **Stream-aligned** | Aligned to a single, valuable stream of work — a product, a service, a user journey, a persona. Owns its slice end to end. | **Yes** — this is the default team type; most teams in the org should be this |
| **Platform** | Provides a compelling internal product (self-service infrastructure, tooling, APIs) that reduces the cognitive load of stream-aligned teams, so they don't each have to become experts in deployment pipelines, cloud infra, or shared services | Exists specifically *in service of* stream-aligned teams — its success metric is stream-aligned team velocity, not its own feature list |
| **Enabling** | Helps stream-aligned teams close a gap in a specific technical or product domain — new tools, new practices, specialist research — through active coaching over a bounded time, then withdraws | Temporary engagement by design; an enabling team that never leaves has quietly become a bottleneck or a dependency |
| **Complicated-subsystem** | Builds and maintains a part of the system that requires deep specialist knowledge most other engineers don't have and shouldn't need (a video codec, a pricing/ratings engine, a real-time matching algorithm) | Exists only where the domain genuinely demands rare specialist depth — not a catch-all for "the team that owns the hard stuff" generally |

### Interaction modes — how two teams should relate

| Mode | What it looks like | When it's right | When it's wrong |
|---|---|---|---|
| **Collaboration** | Two teams work closely and continuously together for a bounded period — high-bandwidth communication, blurred responsibility | Discovering something new together (a new API contract, an unclear domain boundary) | Left in place indefinitely — collaboration has a real cost (both teams carry the coordination overhead), so it should have an explicit end date |
| **X-as-a-Service** | One team consumes another's well-defined service or API with minimal ongoing communication | The providing team's offering is mature, documented, and self-service (this is the mode a Platform team should be in with most stream-aligned teams) | The "service" isn't actually self-service yet — forcing this mode too early just produces a ticket queue disguised as an API |
| **Facilitating** | One team (usually Enabling) actively helps another team learn or adopt something, removing blockers, without doing the work for them | A stream-aligned team needs to level up a specific capability | Ongoing indefinitely — Facilitating that never ends means the enabling team has become a permanent crutch, not a temporary boost |

A fourth informal mode sometimes noted in practitioner discussion — the team API — is the idea that every team should be able to state, explicitly, how other teams are meant to interact with them (which interfaces are stable, what docs exist, what's the escalation path), whether or not the team itself is formally "Platform."

### Diagnosing a bad topology

Two patterns to watch for: a **Stream-aligned team drowning in cognitive load** because it's been handed responsibility for a Complicated Subsystem it doesn't have the specialist depth for (fix: spin out a Complicated-subsystem team, or buy/adopt an external one); and two teams stuck in permanent **Collaboration mode** because the interface between them was never actually defined (fix: push toward X-as-a-Service by investing in a real, documented, self-service interface).

## Example

An e-commerce company has a single "Checkout" stream-aligned team also responsible for maintaining its own Kubernetes deployment pipelines, load-balancer configuration, and cloud cost optimization — on top of shipping checkout features. The team is stalled: most sprint capacity goes to infra firefighting, not checkout improvements (a clear cognitive-load overload, mixing genuine stream-aligned work with what should be Platform work). The fix: stand up a Platform team responsible for a self-service deployment and infra layer used by every stream-aligned team in the company, interacting with Checkout in X-as-a-Service mode — Checkout deploys through a documented, self-service pipeline without needing a ticket or a meeting. Separately, Checkout's fraud-detection logic requires deep, rare expertise in real-time risk scoring; rather than asking Checkout engineers to become fraud specialists on top of everything else, a small Complicated-subsystem team owns the fraud-scoring engine and exposes it to Checkout as a clean API call — Checkout doesn't need to understand the model internals, just the interface.

## Applying it for a client

Start by mapping the client's *actual* team interactions (not the org chart) against the three modes — most consulting value here comes from finding teams stuck in permanent, undocumented Collaboration mode that should have graduated to X-as-a-Service months ago, because nobody ever built the self-service interface that would let them. When a client wants to build a platform team, set the expectation explicitly that its job is to make itself boring and self-service, not to become a second engineering department that stream-aligned teams file tickets to — if a "platform team" behaves like a ticket queue, it hasn't actually adopted the model, it's just relabeled a shared-services team. Use the cognitive-load lens as a direct diagnostic question in interviews: ask engineers on a struggling team to list every distinct domain/system they're expected to understand — a long, sprawling list is usually the real root cause behind complaints that read on the surface as "we need more headcount" or "we need better process."

## Watch-outs

- Calling a shared-services team "Platform" without actually investing in self-service maturity — Platform's defining trait is the X-as-a-Service interaction mode; a team still fielding ad hoc requests through tickets or Slack DMs is not yet a Platform team in this model's sense, whatever its name.
- Enabling teams that never sunset — the model explicitly frames Enabling engagements as temporary; a permanent Enabling team is usually either secretly Platform (build the self-service interface) or secretly Complicated-subsystem (own the thing outright) in disguise.
- Overusing Complicated-subsystem as a label for "the team that does the hard stuff" broadly — it's meant for domains genuinely requiring rare specialist knowledge that other engineers *shouldn't* need to acquire, not just "code we consider difficult."
- Skipping the interface/API design work needed to move a pair of teams from Collaboration to X-as-a-Service — teams don't graduate out of high-touch collaboration automatically; it requires deliberate investment in documentation and self-service tooling.
- Treating the four team types as a rigid, final org chart rather than a fluid model — Team Topologies explicitly expects team types and interaction modes to evolve as a product and organization mature; a topology review should be periodic, not one-and-done.

## Related

- [spotify-model.md](spotify-model.md) — an earlier, less prescriptive pattern aimed at the same underlying problem (team autonomy at scale); Team Topologies gives sharper vocabulary for the interaction-mode friction Spotify's whitepaper left implicit.
- [org-design-star-model.md](org-design-star-model.md) — cognitive-load overload in a Stream-aligned team is often a Structure-point misdesign (wrong team boundaries) compounded by a Processes gap (no defined interface between teams).
- [raci-rapid-daci.md](raci-rapid-daci.md) — defining a "team API" (what other teams can expect and who to ask) is a decision-rights exercise at the team-boundary level, not just the individual-decision level these frameworks usually address.
