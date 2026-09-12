---
domain: product-management
concept: Product-Led Growth (PLG)
source: research — OpenView Partners (Blake Bartlett, 2016) / Wes Bush, "Product-Led Growth" (2019)
tags: [growth, gtm, saas, acquisition, retention]
---

# Product-Led Growth (PLG)

Product-Led Growth is a go-to-market motion where the product itself — not a sales team or a marketing campaign — is the primary driver of acquisition, conversion, expansion, and retention: users self-serve their way to value, usually through a free trial or freemium tier, before or instead of ever talking to a salesperson. The term was coined at OpenView Partners around 2016 and codified into a repeatable playbook by Wes Bush's 2019 book of the same name. A consultant needs it to distinguish from sales-led growth (a rep drives the deal) and marketing-led growth (paid/content marketing drives top-of-funnel, sales still closes) — and to know when PLG is genuinely the right motion versus when a client is chasing a trend that doesn't fit their sale.

## When to use

- Evaluating or designing a SaaS go-to-market motion for a product with a short time-to-value and a low-to-mid price point, where a sales team's cost-per-deal would exceed what the deal is worth.
- A client's funnel routes every trial or signup through a sales rep by default, leaving self-serve conversion on the table for buyers who'd rather not talk to anyone before trying the product.
- Designing pricing and packaging — PLG requires explicit choices (what's free, what's gated) that a sales-led pricing model never has to make.
- Diagnosing why a product with strong usage metrics isn't converting to revenue — often a value gate placed at the wrong point in the user's journey.
- As a fit test, not just a playbook — complex, high-ACV, multi-stakeholder enterprise software often still needs a sales-assisted or hybrid motion (see Watch-outs).

## How it works

### The flywheel — acquisition, conversion, expansion, retention, all product-driven

- **Acquisition** — the product markets itself via word-of-mouth, viral loops ("invite your team" prompts, shared documents/links exposing the product to non-users), and SEO-friendly free-tier usage (public shared pages indexed by search), instead of or alongside paid ads.
- **Conversion** (free → paid) — self-serve upgrade flow triggered by hitting a usage limit or needing a gated feature, sold in-product rather than by a rep.
- **Expansion** — existing paid users grow spend by adding seats or usage themselves, typically without a renewal negotiation, because usage-based or seat-based billing scales automatically.
- **Retention** — because users self-selected into the product by getting real value, retention is driven by habitual usage rather than contractual lock-in.

### Free trial vs. freemium — the two dominant models

| | Free Trial | Freemium |
|---|---|---|
| Access | Full (or near-full) product, time-limited (e.g., 14 days) | Limited feature set or usage cap, unlimited time |
| Best fit | Fast time-to-value provable within the trial window | A genuinely useful core loop at zero cost, with a natural usage ceiling to gate |
| Conversion driver | Time pressure (trial ending) | Usage-limit or feature-gate pressure |
| Risk | Users who don't reach value in time churn before seeing it | Users camp in the free tier indefinitely if the gate is too generous |

### Where to place the value gate — the central design decision

Bush's framework asks three questions before gating any feature or limit:

1. Does giving this away free drive enough word-of-mouth/virality to be worth it?
2. Does experiencing this for free create the "aha moment" needed to prove value?
3. Is this something users would pay to unlock once they've already felt the value?

Gate too early (before the aha moment) and users churn without ever seeing value; gate too late (fully served for free) and there's no reason left to convert.

### Product Qualified Leads (PQLs)

A PQL is a free or trial user whose in-product behavior — invited 3+ teammates, hit 80% of a usage cap, used a specific high-intent feature — indicates strong buying intent. This replaces or supplements marketing/sales lead scoring with usage-based lead scoring; in a hybrid PLG+SLG motion, sales reaches out only once a user becomes a PQL, not at signup.

### Metrics that matter (cross-reference [aarrr-pirate-metrics.md](aarrr-pirate-metrics.md) — PLG is a philosophy for optimizing that same funnel primarily through the product)

Time-to-value, activation rate, free-to-paid conversion rate, expansion revenue / net revenue retention (NRR), and virality coefficient (how many new users each existing user brings in).

## Example

Slack is the canonical case: teams start using it free with no sales conversation; channels and DMs create viral pull as invited teammates join organically; the value gate sits at message-history limits and integration caps (not core messaging, which stays usable to preserve the daily habit driving retention); expansion happens automatically as a growing team needs more paid seats or unlimited history. Sales gets involved only for large enterprise deals — a hybrid PLG+SLG motion at scale, not the initial-adoption path.

A smaller, numeric example: a project-management tool gets 10,000 free signups/month; time-to-value averages 2 days (first project created, first collaborator invited). 22% become PQLs by month 1 (defined as: 3+ projects created AND 2+ collaborators invited). Of PQLs, 35% self-serve convert to paid within 60 days with no sales contact; the remainder (larger accounts, 10+ seats) route to a small sales-assisted team, converting at a further 18%. The product does the qualifying and most of the converting; sales is reserved for accounts where a human conversation actually adds value.

## Applying it for a client

Map the client's current funnel against the flywheel (Acquisition/Conversion/Expansion/Retention) and identify which stage is currently sales-dependent without needing to be — the most common finding is a demo-gated trial that would convert far more users if opened to self-serve first, with sales reserved for the PQL segment. Run the three-question value-gate test explicitly against the client's current free/paid split; clients regularly discover they've gated the exact feature that would have produced their aha moment, killing conversion before it can happen. For a client with a genuinely complex, multi-stakeholder enterprise sale (procurement review, security review, high ACV), don't force pure PLG — recommend a hybrid motion where product-led adoption drives bottom-up usage and PQL signals trigger a sales-assisted upsell, rather than trying to remove sales from a sale that needs it. Define PQL criteria jointly with sales, not product alone — a PQL definition sales doesn't trust won't get acted on regardless of how well-instrumented the usage data is.

## Watch-outs

- PLG is not a universal fit — high-ACV, high-complexity, high-compliance-risk enterprise software usually still needs a sales-led or sales-assisted motion; forcing self-serve onto a genuinely complex sale adds friction without removing the need for a rep.
- A too-generous freemium tier (gate placed too late) removes the incentive to convert — watch for a growing free-user base with flat or declining paid conversion as the specific symptom.
- PLG shifts, rather than eliminates, go-to-market cost — instrumentation, in-product onboarding design, and self-serve billing infrastructure are real, ongoing investments, not a free replacement for a sales team.
- Optimizing pure acquisition/virality metrics without a matching retention motion produces a leaky-bucket flywheel — cross-check PLG wins against [aarrr-pirate-metrics.md](aarrr-pirate-metrics.md)'s Retention stage before declaring a PLG initiative successful.

## Related

- [north-star-metric.md](../product-management/north-star-metric.md) — many PLG companies' NSM is a usage-based metric (e.g., "weekly active teams") precisely because it doubles as the PQL signal.
- [aarrr-pirate-metrics.md](../product-management/aarrr-pirate-metrics.md) — PLG is a philosophy for driving that same five-stage funnel primarily through in-product mechanics rather than sales/marketing.
- [business-model-canvas.md](../product-management/business-model-canvas.md) — PLG requires explicit choices in the Channels and Customer Relationships blocks (self-service, automated) that differ sharply from a sales-led BMC.
