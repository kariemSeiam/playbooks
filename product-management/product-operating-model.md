---
domain: product-management
concept: Product Operating Model (Empowered Product Trio)
source: research — Marty Cagan / Silicon Valley Product Group, "Empowered" (2020) and "Transformed" (2024)
tags: [product-org, empowerment, product-trio, outcomes]
---

# Product Operating Model (Empowered Product Trio)

The Product Operating Model is Marty Cagan and SVPG's name for organizing small, durable, cross-functional teams — product manager, designer, and engineer, "the trio" — around a problem to solve, with the autonomy to figure out the best solution, rather than around a prioritized list of features handed down to build. Cagan contrasts this explicitly with the "feature team" model, where product management exists mainly to gather requirements and write specs, and prioritization (even solution design) is effectively owned by stakeholders or executives rather than the trio itself. A consultant needs this distinction because a company can have a full product org — PMs, designers, engineers, a roadmap — and still be running feature teams in substance, which is usually the actual reason "we have product people but we're not innovating."

## When to use
- Diagnosing why a company with a complete product org still isn't innovating — most often because teams are structured as feature factories (measured by output/velocity) rather than empowered teams (measured by outcomes).
- Designing or restructuring a product organization, or shifting a company from project-based/waterfall delivery toward genuine product operation.
- Explaining to executives why "just tell the team what to build" undermines the exact expertise (customer insight, technical feasibility judgment) they're paying a product team to have.
- Setting up the discovery habits ([continuous-discovery.md](continuous-discovery.md)) and OKRs ([okrs.md](okrs.md)) that only function correctly when a team actually has authority to act on what discovery reveals — installing discovery onto a disempowered feature team just produces research nobody can act on.

## How it works

### Feature team vs. empowered team — the central distinction
| | Feature Team | Empowered (Product) Team |
|---|---|---|
| Given | A roadmap of features/projects to build, on a schedule | A problem to solve / outcome to own |
| Success measured by | Output — did we ship the roadmap on time | Outcome — did the business/customer result actually move |
| Who decides what to build | Stakeholders/executives/sales; PM writes it up | The trio, informed by continuous discovery |
| PM's actual job | Project manager / requirements-gatherer | Product strategist, responsible for value and viability of what gets built |
| Engineer's role in discovery | Absent — hears the spec after decisions are made | Present during discovery — helps assess feasibility and often co-generates solutions |

### The Product Trio — three roles, jointly responsible for discovery
- **Product Manager** — responsible for value (is this worth building for the business) and viability (does it work within legal, financial, and business constraints).
- **Product Designer** — responsible for usability (can real users actually figure out and enjoy using this).
- **Engineering Lead** — responsible for feasibility (can we actually build this with the time, skills, and technology we have) — critically, present *during* discovery, not handed a finished spec afterward, because feasibility constraints often reshape which solution is even worth prototyping.

### The four risks every empowered team is responsible for de-risking
Cagan frames product discovery as risk-reduction across four dimensions, all owned jointly by the trio: **Value risk** (will customers buy/use this), **Usability risk** (can users figure out how to use it), **Feasibility risk** (can engineers build it with available time/skills/tech), **Business Viability risk** (does it work for sales, marketing, finance, legal, compliance, and partnerships).

### What empowerment actually requires, structurally
1. Teams are organized around a durable *problem space* (e.g., "checkout," "onboarding"), not a temporary project — expertise and context compound over time instead of resetting with every new initiative.
2. Teams are given problems or outcomes (a Key Result to move — see [okrs.md](okrs.md)), not a feature list, with the trio owning how to hit it.
3. Product strategy sets the *context* — which outcomes matter, in what order, and why — letting teams make good local decisions without every choice needing escalation. Cagan calls this giving teams "the why," not just "the what."
4. Genuine two-way accountability: teams get freedom to choose their solution but remain accountable for whether the outcome actually moved — empowerment isn't license to work on whatever seems interesting.

### Leadership's changed role
The manager's job shifts from assigning tasks to coaching the trio — especially the PM — on judgment: how to run discovery well, how to read data, how to make the value/viability call. Cagan is explicit that most organizations under-invest in this coaching function, promoting people into PM roles without ever teaching them how to actually do discovery.

## Example

A feature-team model hands its checkout team a roadmap item: "Add Apple Pay by Q3" — an output decided by an executive who saw a competitor announce it. The team ships it on schedule, but checkout conversion doesn't move, because Apple Pay wasn't the actual barrier; an unexpected shipping-cost reveal at the final step was driving cart abandonment. Contrast: an empowered checkout team is instead given the outcome "reduce cart abandonment from 68% to 55%" (a Key Result). Through continuous discovery — PM, designer, and an engineer sitting in on interviews together — the trio finds the real value risk is the late shipping-cost surprise, not a missing payment method, and builds an upfront shipping estimator instead: a solution nobody had put on the original feature roadmap, and abandonment actually drops.

## Applying it for a client

Before recommending any restructuring, diagnose which model the client currently runs with one question: "who decided what your team is building this quarter, and how?" If the answer is "an executive or sales handed us a feature list," the client is running a feature-team model regardless of the job titles on the org chart. Introduce empowerment incrementally — pilot it on one team, given one real outcome to own for a full quarter, rather than restructuring the whole org at once; a company-wide mandate without a proven internal example usually reverts under pressure at the first missed deadline. Pair the restructuring explicitly with [okrs.md](okrs.md) (to define the outcome the team owns) and [continuous-discovery.md](continuous-discovery.md) (to give the trio the weekly habit that makes empowerment actionable) — handing a team an outcome without the discovery habit just produces an empowered team with no information to act on. For the client's executive layer, reframe their job description alongside the team's: in this model, leadership's job becomes setting compelling outcomes and context, not approving individual feature specs — a leadership team unwilling to give up spec-approval will quietly re-collapse the model back into a feature-team structure no matter how the org chart is redrawn.

## Watch-outs

- Empowerment without accountability isn't the model — a team given an outcome but never actually held to whether it moved (or praised regardless) is an unmanaged team, not an empowered one.
- Reorganizing the org chart into "trios" without changing what teams are given (a feature list vs. a problem) changes nothing — the model is defined by what teams are asked to solve, not by team composition alone.
- Engineers treated as "implementation only," absent from discovery, quietly recreates the feature-team pattern even under a trio label — feasibility judgment needs to be present *while* solutions are being shaped, not applied afterward as a veto.
- This is a genuinely disruptive organizational change — staffing model, leadership behavior, how success is measured. Treat a client's request to "just try Cagan's model" with real caution, and recommend a single-team pilot with a clearly measurable outcome before any company-wide rollout.

## Related

- [continuous-discovery.md](../product-management/continuous-discovery.md) — the weekly-discovery habit and Opportunity Solution Tree are the concrete discovery mechanics an empowered trio runs; this note is the organizational structure that makes that discovery actionable.
- [okrs.md](../product-management/okrs.md) — outcomes given to empowered teams are typically framed and tracked as OKRs.
- [product-management-fundamentals.md](../product-management/product-management-fundamentals.md) — the feature-team/empowered-team distinction is a sharper, structural version of that note's "build the right product vs. build it right" twin objective.
- [scrum-framework.md](../product-management/scrum-framework.md) — Scrum defines the delivery rhythm an empowered team still runs, but the trio's authority over discovery and solution choice is the empowerment layer Scrum alone doesn't grant.
