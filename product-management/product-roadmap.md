---
domain: product-management
concept: Product Roadmap
source: sources/product-management/civiconnectors-product-management.pdf.card.md
tags: [roadmap, planning, strategy, tools]
---

# Product Roadmap

A roadmap is a shared source of truth outlining the vision, direction, priorities, and progress of a product over time — a plan of action that aligns the organization around short- and long-term goals and how they'll be achieved. It sits between the vision (the destination) and the prioritized backlog (the individual decisions) — the roadmap is the connective plan that turns one into the other.

## When to use

Build or update a roadmap whenever the vision and prioritized feature list need to be communicated as a timeline to a specific audience — engineering, executives, IT, or marketing each need a *different* roadmap, because they need different information at a different altitude. Use the review-cadence guidance below to decide how often to revisit it, based on whether the product is early-stage or mature.

## How it works

**Four types of roadmap, distinguished by focus and audience:**

1. **Product Roadmap** — Focus: outlines the vision, evolution, and future state of a product, prioritizing features/initiatives based on user needs, business goals, and market trends. Audience: product managers, developers, designers, and other stakeholders in the product development process. Example: shows upcoming features like "new login system" or "enhanced search functionality" with target release dates.

2. **Business Roadmap** — Focus: maps high-level strategic goals and objectives of the business, outlining key initiatives and milestones to achieve them. Audience: executives, senior management, strategic decision-makers. Example: shows strategic initiatives like "entering a new market" or "launching a new product line" with target completion timelines.

3. **Technology Roadmap** — Focus: defines the planned evolution and direction of the organization's technology infrastructure, outlining upcoming adoption, upgrades, or integrations. Audience: IT professionals, CTOs, and stakeholders in technology strategy/implementation. Example: shows plans to "migrate to a cloud-based infrastructure" or "implement a new security system" with target deployment dates.

4. **Marketing Roadmap** — Focus: outlines marketing campaigns, initiatives, and tactics designed to achieve specific marketing goals (brand awareness, lead generation, customer acquisition). Audience: marketing professionals, content creators, marketing strategy/execution stakeholders. Example: shows upcoming campaigns like "launching a social media campaign" or "releasing a new white paper" with target launch dates.

**Tools to build a roadmap with:** Trello, Jira, Notion, Airtable, Aha! Roadmaps, ClickUp.

**Review cadence — the key operational rule:**
- **Early stage** (new products, early development): review **more frequently**, weekly or bi-weekly. This allows greater flexibility and adaptation as you gather user feedback and learn more about market needs.
- **Mature stage** (established products with a well-defined user base and market position): reviews can happen **less frequently**, monthly or quarterly. Even mature products should still be reviewed regularly to stay aligned with evolving market trends and user needs — "less frequent" doesn't mean "stop reviewing."

## Example

A pre-launch startup's product roadmap gets revisited every two weeks, because each round of user interviews and each sprint's usage data can genuinely change what "next quarter" should contain. Three years later, once the same product has a stable, large user base, the roadmap moves to quarterly review — the fundamentals (core segments, core value proposition) are validated and don't shift week to week, so weekly review would just be churn without new information to act on.

## Applying it for a client

Ask which of the four roadmap types the client actually needs *before* building anything — a common failure is handing a CEO a product roadmap full of sprint-level feature names when they needed a business roadmap with market-entry milestones, or handing engineering a business roadmap with no technical specificity to plan sprints against. For a startup client early in its life, push for the weekly/bi-weekly review cadence explicitly — founders often set a roadmap once during a strategy engagement and then treat it as fixed for a year, which defeats the purpose at the exact stage where market feedback should be reshaping it fastest. For a mature clinic or established brand client, a quarterly cadence tied to a business roadmap (new service lines, new locations) is usually the right altitude — don't import startup-speed review rituals onto a business that isn't changing that fast; it creates review fatigue without benefit.

## 2024→2026: Living decision systems, and a two-stream question

*Status: the "living decision system" shift is emerging-but-credible; the agentic-user framing below is trendy-unproven — treat it as a flag to watch, not an established practice.*

The roadmap-as-static-document model this note describes is increasingly being displaced by the roadmap as a living decision system — a continuously re-sorted view (see [now-next-later-roadmap.md](now-next-later-roadmap.md)) tied directly to a running Opportunity Solution Tree ([continuous-discovery.md](continuous-discovery.md)) and the current period's OKRs ([okrs.md](okrs.md)), rather than a document finalized once per planning cycle and presented as fixed. The practical difference: instead of a quarterly roadmap review meeting reconciling what happened against what was planned, the roadmap tool itself reflects discovery findings and OKR scoring changes as they happen, so "the roadmap" and "the current state of what we've learned" are the same artifact rather than two things a PM has to keep in sync manually.

A more speculative idea worth naming, but not yet treating as settled practice: as products increasingly expose APIs and MCP-style interfaces that let AI agents act as direct consumers of a product — not just humans clicking through a UI — some practitioners are starting to argue roadmaps need a "two-stream" view: one stream of outcomes for human users, a separate stream for agentic/API consumers, whose needs (rate limits, schema stability, machine-readable error semantics) don't map cleanly onto a human-facing feature roadmap. This is genuinely unproven as a roadmapping discipline — there's no equivalent yet to the well-established four-roadmap-type distinction (Product/Business/Technology/Marketing) above for it, and a consultant should surface it as an open question to watch for a client building agent-facing surfaces, not present it as a framework with settled best practices.

## Watch-outs

- A roadmap is not the same document as the prioritized backlog (see [prioritization-techniques.md](prioritization-techniques.md)) — the roadmap shows the *what and roughly when* at a stakeholder-appropriate altitude; the backlog holds the granular, frequently re-ranked list of individual items.
- Presenting a roadmap with fixed dates to non-technical stakeholders invites those dates to be treated as commitments rather than current best estimates — be explicit about which type of roadmap (and which audience) you're building, since a business roadmap's "milestones" read very differently to executives than a product roadmap's "target release dates" do to engineers.
- Reviewing too rarely on a mature product isn't safe just because the product is stable — market trends and user needs still shift, and "we haven't touched the roadmap in a year" is itself a risk signal, not a sign of a settled strategy.

## Related

- [product-vision.md](../product-management/product-vision.md)
- [prioritization-techniques.md](../product-management/prioritization-techniques.md)
- [scrum-framework.md](../product-management/scrum-framework.md)
