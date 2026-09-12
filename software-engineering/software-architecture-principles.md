---
domain: software-engineering
concept: Separation of concerns, coupling & cohesion, stable-contract encapsulation
source: research — synthesized from 2026 software architecture practice guides (Codewave's 12 Principles, industry references on coupling/cohesion and encapsulation), 2026
tags: [architecture, separation-of-concerns, coupling, cohesion, modularity, single-responsibility]
---

# Software architecture principles: separation of concerns, coupling, cohesion

These four ideas — separation of concerns, single responsibility, loose
coupling/high cohesion, and stable-contract encapsulation — aren't four
separate rules; they're one idea (contain the blast radius of a change)
viewed from four angles. A system built on them lets a change to one part
stay a change to one part. A system built without them turns every change
into a research project: touch one thing, discover three other things
depend on its internals, and now the "small fix" is a multi-file rewrite.
That escalation — small intended change, unpredictable actual blast
radius — is the concrete cost these principles exist to prevent.

## When to use

- Deciding where a new piece of logic belongs — which module, service, or
  layer owns it — before writing it, not after it's already tangled into
  the wrong place.
- A codebase where changes routinely take longer than they should because
  touching one thing breaks something apparently unrelated.
- Designing the boundary between two systems (two services, a frontend
  and a backend, a plugin and its host) — where the actual contract
  between them needs to be decided explicitly, not left implicit.
- Reviewing whether an existing module has grown too many unrelated
  reasons to change — a sign it needs splitting before the next feature
  makes it worse.

## How it works

**Separation of concerns** — divide a system into parts, each responsible
for one kind of concern, typically along lines like: domain logic
(business rules), application/service layer (orchestration),
infrastructure (databases, external APIs, file systems), and presentation
(UI, API responses). The test: can the infrastructure layer be swapped
(a different database engine, a different email provider) without
touching domain logic at all? If yes, the concerns are actually separated;
if the swap requires editing business-rule code, they're mixed.

**Single responsibility** — each module or service should have one reason
to change. Not "one function" — one *reason*. A service that changes when
pricing logic changes, when notification templates change, AND when
payment provider integration changes has three responsibilities wearing
one name, and every one of those unrelated changes now risks the other
two.

**Coupling and cohesion** — two sides of the same measurement. Coupling is
how much a module depends on another module's internals; cohesion is how
tightly a module's own contents belong together. The goal is always the
same shape: **low coupling, high cohesion** — modules that are internally
unified around one purpose, and externally connected to each other
through the smallest, most stable surface possible. High coupling shows up
concretely as: two services writing to the same shared database table, or
a shared library whose internal changes ripple out and break unrelated
consumers.

**Stable-contract encapsulation** — the practical mechanism that makes low
coupling actually hold over time: modules and services expose a versioned,
deliberately-designed contract (an API, a well-defined function
signature) and never let a consumer depend on internal structure directly
(no reaching into another service's database, no importing another
module's private internals). This is what allows one side of a contract
to change its own implementation completely without requiring the other
side to change anything.

## Example

A checkout module in an e-commerce system owns pricing, tax calculation,
and payment-flow orchestration — genuinely related concerns, all part of
"the moment of checkout," which is why they live in one cohesive module
rather than being split further. The inventory service, the shipping
service, and the customer-notification service each integrate with
checkout only through its published API (`POST /checkout/complete`, its
response schema) — none of them queries checkout's database tables
directly. When the checkout team swaps their internal pricing engine for
a new one, or migrates from one database to another, none of the three
other services need to change anything, because none of them ever
depended on checkout's internals — only on its stable, published contract.

## Applying it for a client

Start by asking "what changes together, and what changes for different
reasons?" — not by drawing boxes first. If two pieces of logic always
change in lockstep (a validation rule and the form that enforces it),
they likely belong in the same module; if two pieces of logic live in the
same file but change for completely unrelated reasons (order processing
and email templates), that's the signal to split, regardless of how small
either piece currently is. When reviewing an existing client codebase for
a refactor, look first for shared-database coupling (two services reading
or writing the same tables directly) — it's the single most common,
highest-cost violation, because it means neither service can safely
change its own schema without breaking the other, and it's invisible
until someone tries. Recommend fixing it via a published API or event
contract, not by "being careful" — careful doesn't scale past the person
who was careful leaving the project.

## Watch-outs

- Separation of concerns can be over-applied — splitting a module that is
  genuinely one cohesive concept into three files "for organization"
  adds indirection without reducing coupling, since the three files still
  change together every time. Split along reasons-to-change, not along an
  arbitrary size limit.
- Low coupling is not zero coupling — some coupling is required for any
  system to actually do anything together; the goal is coupling through a
  stable, explicit contract, not the elimination of all dependency.
- A "shared library" is a common disguised violation: it looks like good
  reuse, but if its internal changes force simultaneous updates across
  every consumer, it's tight coupling wearing the shape of a best
  practice. The fix is versioning the shared library's contract the same
  way a service would version its API.
- Encapsulation only holds if it's enforced structurally (a real API
  boundary, a real package boundary) — "please don't import our
  internals" as a comment or a wiki note is not encapsulation, it's a
  request that will eventually be ignored under deadline pressure.

## Related

- [rest-api-design.md](rest-api-design.md) — the concrete mechanism (an HTTP API contract)
  that makes stable-contract encapsulation enforceable between services,
  not just a design intention.
- [ai-agent-architecture-patterns.md](ai-agent-architecture-patterns.md) — multi-agent orchestration is the
  same coupling/cohesion tradeoff applied to agents instead of services:
  each specialist agent needs a narrow, stable contract with the
  orchestrator, for the same reason a checkout service needs one with
  inventory.
