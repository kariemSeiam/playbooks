---
domain: strategy
concept: AI Build vs. Buy
source: 'research — MIT NANDA, "The GenAI Divide: State of AI in Business 2025" (2025)'
tags: [ai, build-buy, adoption, maturity, technology-strategy]
---

# AI Build vs. Buy

AI build-vs-buy is a staged decision framework for how much of an AI capability an organization should build in-house versus buy or partner for, built around empirical evidence that most enterprise GenAI initiatives fail to deliver measurable financial return, and that the failure pattern differs sharply by build/buy choice. MIT's NANDA initiative's 2025 report — based on roughly 150 leader interviews, a 350-employee survey, and analysis of 300 public AI deployments — is the primary empirical anchor: despite $30–40B in enterprise GenAI investment, roughly 95% of organizations saw no measurable P&L impact from their pilots, and vendor partnerships and specialized-tool purchases succeeded at roughly double the rate of internal builds (about 67% versus about 33%). A consultant needs a framework here because "just build it, AI is strategic" and "just buy a tool" are both wrong defaults — the right answer depends on where a specific capability sits relative to the business's actual differentiation.

## When to use
- A client is under pressure — board, competitors, hype cycle — to "do something with AI" without a clear view of which capability to prioritize or how to resource it
- Evaluating whether to build a custom internal AI/ML capability versus adopting a vendor's out-of-the-box AI product or API
- A prior internal AI build has stalled or failed to reach production, and the client needs a diagnostic before trying again
- Budgeting an AI roadmap across multiple initiatives with different strategic importance
- Vendor selection processes where "we'll build it eventually" is being used to justify not committing to any external partnership now

## How it works

**The staged approach: Experiment → Extend → Evolve.**

| Stage | Approach | What it looks like | When appropriate |
|---|---|---|---|
| **Experiment** | Buy / partner | Adopt existing vendor tools and APIs for a bounded pilot, minimal internal engineering investment | Capability is not core differentiation; need to learn fast and cheap whether AI even helps this use case |
| **Extend** | Hybrid | Combine vendor foundation models or platforms with a thin layer of custom integration, prompting, fine-tuning, or workflow logic specific to the business | Use case is proven valuable from Experiment, but needs proprietary data or workflow to deliver real value; full custom build isn't yet justified |
| **Evolve** | Build core | Invest in owned models, infrastructure, or proprietary data pipelines | Capability is a genuine, durable source of competitive differentiation — the specific application no vendor tool can replicate because it depends on proprietary data or workflow |

**Why the default should be "buy" unless core differentiator.** The NANDA findings give the empirical reason to default toward buy/partner rather than build: vendor partnerships succeeded at roughly 67% versus roughly 33% for internal builds. The report attributes much of this gap to what it calls the "learning gap" — the inability of internally-built tools to retain feedback, adapt to context, and improve over time in ways specialized vendor tools, built by teams whose sole focus is that narrow problem, already solve. The practical implication: treat "build" as an expensive, high-risk option that must be earned by evidence of real differentiation, not a default expression of strategic seriousness.

**Where the real ROI showed up.** Contrary to where most GenAI budget was actually spent — the report found more than half of GenAI budgets went to sales and marketing-facing tools — NANDA's research found the biggest realized ROI in unglamorous back-office automation: eliminating business-process-outsourcing spend, cutting external agency costs, streamlining internal operations. This is a useful check on client enthusiasm: the highest-visibility AI use case (customer-facing generative features) is not empirically where the money has actually been made back.

## Example

A mid-size retailer wants an AI customer-service capability. **Experiment:** adopt an off-the-shelf AI helpdesk copilot, vendor-hosted, minimal integration, for 90 days on a subset of ticket types, measuring deflection rate and CSAT — cheap to start, cheap to kill if it doesn't work. If it works, **Extend:** integrate the vendor tool with the retailer's own order and CRM data via API so it can answer order-specific questions, still on the vendor's underlying model but now differentiated by the retailer's proprietary data connection. Only if customer service becomes an explicit strategic differentiator — not the case for most retailers, whose differentiation is merchandising, price, or logistics — would **Evolve** (a custom-trained, owned model) be justified; for the large majority of retailers, staying at Extend indefinitely is the economically correct answer, not a failure to "finish" the journey to build.

## Applying it for a client

For every proposed AI initiative, force the differentiation question explicitly first: is this specific capability the thing the client is best in the world at, their actual economic engine (echoing the Hedgehog Concept logic in [flywheel-effect.md](flywheel-effect.md)), or is it a horizontal capability every competitor can buy the same way? Use [wardley-mapping.md](wardley-mapping.md)'s evolution axis directly here: if the underlying AI capability (document summarization, image classification) has moved to Product/Commodity stage industry-wide, buying is almost always correct; only Genesis/Custom-stage capabilities specific to the client's proprietary data justify a build. Push back hard on "build for control/strategic reasons" as a stated rationale without a differentiation argument behind it — the NANDA data says that instinct is empirically the losing bet two-thirds of the time. Structure the engagement itself in stages matching Experiment → Extend → Evolve, with an explicit stage-gate decision (kill, continue, escalate investment) at each transition rather than committing to an open-ended "AI initiative."

## Watch-outs
- "AI is strategic so we should build it" is not, by itself, a differentiation argument — strategic importance justifies investing attention and budget, not necessarily building the underlying model or infrastructure yourself
- The 95% no-ROI finding is about pilots that stayed pilots — it is not evidence that AI has no value, but that most organizations haven't gotten past Experiment into an integration (Extend) that actually changes a workflow; don't let a client over-read the statistic as "AI doesn't work"
- Buy/partner still requires real internal capability — data governance, integration engineering, vendor management — "buy" is not "do nothing," and organizations that buy a tool without investing in adoption and change management fail just as often as failed internal builds
- Vendor lock-in and data-portability risk grow the longer a client stays in Extend without revisiting whether the capability should eventually move toward Evolve — periodically re-ask the differentiation question rather than treating the stage as permanent
- The build/buy decision is per-capability, not per-company — a single organization should expect to be in Experiment on some initiatives, Extend on others, and Evolve on one or two truly differentiating ones, simultaneously

## Related
- [wardley-mapping.md](../strategy/wardley-mapping.md) — the evolution axis (genesis to commodity) is the direct mechanism for deciding which AI capability, if any, has earned a "build" decision
- [ai-maturity-models.md](../strategy/ai-maturity-models.md) — build-vs-buy is one specific decision inside the broader organizational AI-maturity journey that note maps
- [crisp-dm-mlops.md](../strategy/crisp-dm-mlops.md) — once a client has earned an "Evolve" (build) decision, that note's process and lifecycle framework governs how the actual model gets built and operated
