---
domain: strategy
concept: AI Maturity Models
source: 'research — Andrew Ng, *AI Transformation Playbook* (Landing AI, 2018); Gartner, AI Maturity Model; McKinsey, *Rewired: The McKinsey Guide to Outcompeting in the Age of Digital and AI* (Lamarre, Smaje, Zemmel, 2023)'
tags: [ai, maturity, transformation, adoption, capability]
---

# AI Maturity Models

AI maturity models are staged frameworks for diagnosing how far an organization has actually progressed in adopting AI — from no formal capability to AI being embedded in how the business competes — used to sequence investment and avoid both under-ambition (stuck running isolated pilots forever) and over-ambition (attempting enterprise-wide transformation before basic foundations exist). Three frameworks matter to a consultant, each with a different emphasis: Andrew Ng's practitioner playbook sequences concrete actions, Gartner's model diagnoses where a client sits today, and McKinsey's model names the capability dimensions that must mature together.

## When to use

- Diagnosing why a client's AI efforts feel stuck — usually because a later stage's moves are being attempted before an earlier stage's foundations exist
- Structuring a multi-year AI roadmap for a board or CEO, sequencing investment realistically instead of jumping straight to "transformational"
- Benchmarking a client's current state against industry peers to calibrate urgency
- Justifying near-term, unglamorous investments — talent, data infrastructure, training — against pressure to show flashy customer-facing AI wins immediately
- Combined with [ai-build-vs-buy.md](ai-build-vs-buy.md) — maturity stage strongly predicts which build/buy default is realistic; an organization at Gartner's Awareness stage has no business attempting a custom Evolve-stage build

## How it works

### Andrew Ng's AI Transformation Playbook — 5 sequential steps

Aimed at company leadership as an execution sequence, not a diagnostic:

1. **Execute pilot projects to gain momentum** — chosen for feasibility and visible internal proof, not necessarily the largest business impact; success builds organizational belief before asking for bigger bets
2. **Build an in-house AI team** — early pilots can lean on outside partners for speed, but durable capability requires bringing expertise in-house over time
3. **Provide broad AI training** — not just for the AI team; educate the wider non-technical workforce on what AI can and can't do, so adoption doesn't bottleneck on a handful of specialists
4. **Develop an AI strategy** — once the organization has real pilot experience and trained people, define where AI creates genuine competitive advantage (echoing the differentiation question in [ai-build-vs-buy.md](ai-build-vs-buy.md)), rather than defining strategy on day one before anyone has hands-on experience
5. **Develop internal and external communications** — manage investor and government relationships, marketing, talent attraction and retention, and critically, internal communication addressing employee fears about AI and job displacement

The sequencing is deliberate and often gets reversed by clients under pressure: Ng's point is that strategy (step 4) comes *after* pilot experience and trained people (steps 1–3), because a strategy written by people with no hands-on AI experience is usually wrong.

### Gartner's AI Maturity Model — 5 levels

A diagnostic staging model — where does the organization actually sit today:

| Level | Name | Characteristic |
|---|---|---|
| 1 | **Awareness** | Recognizes AI's potential; no formal strategy; ad hoc discussion; no data governance foundation |
| 2 | **Active** | Isolated pilot projects and proofs of concept; still experimental, not integrated |
| 3 | **Operational** | AI integrated into specific, defined business workflows; initial standards and improving data practices |
| 4 | **Systemic** | AI deployed across multiple functions with measurable ROI; becoming fundamental to how parts of the business operate, not just a bolted-on tool |
| 5 | **Transformational** | AI reshapes decision-making, operating model, and competitive advantage; embedded in the organization's DNA |

Most organizations sit at Level 1–2; Level 5 is rare. The practical use is diagnostic honesty — a client that has run a few pilots (Level 2) but describes itself as "AI-transformed" is miscalibrated, and a roadmap built on that miscalibration fails the same way premature build decisions fail in [ai-build-vs-buy.md](ai-build-vs-buy.md).

### McKinsey's "Rewired" building blocks — 6 dimensions

Rather than sequential stages, McKinsey's *Rewired* frames AI-at-scale as six capability dimensions that must mature together, not in isolation: **strategy** (AI aligned to and derived from overall corporate strategy, not a bolt-on initiative), **talent** (the right people in the right roles — AI-literate operators embedded in the business, not just data scientists), **operating model** (redeploying resources quickly, empowering teams to act without excess dependency, embedding technical talent directly in business units rather than a walled-off central lab), **technology**, **data** (quality and architecture, not just volume), and **adoption and scaling** (actually changing how people work day to day, not just shipping a tool). McKinsey's own finding echoes Ng's sequencing: companies with the greatest bottom-line impact invest across all six dimensions together, rather than over-indexing on technology and data while neglecting talent and operating-model change.

## Example

A logistics company runs three isolated route-optimization pilots (Gartner Level 2 — Active) and its CEO wants to announce an "AI-first" transformation to the board. Applying Ng's sequence: before writing an enterprise AI strategy (step 4), the company still needs an in-house team (step 2, currently outsourced entirely to a vendor) and broad training so operations staff actually trust and use the pilot's recommendations (step 3, currently skipped). Applying McKinsey's six blocks as a coverage check: the company has invested heavily in technology and data (the route-optimization models) but has no operating-model or talent workstream — dispatchers still override the model's recommendations by default because no one redesigned their workflow or incentives around it. The roadmap gets resequenced to build the missing foundations before any Level 4 "systemic" claim is credible.

## Applying it for a client

Use Gartner's 5 levels first, as a quick, honest diagnostic conversation with leadership — get agreement on which level the organization is actually at before anything else, since most roadmap mistakes stem from a client believing they're a level or two ahead of reality. Then sequence the roadmap using Ng's 5 steps, explicitly resisting pressure to write "the AI strategy" (step 4) before the organization has real pilot experience and some in-house capability (steps 1–3) — this is the single most common client request to redirect. Use McKinsey's six building blocks as a coverage check on any roadmap: if the plan invests heavily in technology and data but has no talent or operating-model workstream, flag the imbalance explicitly, since McKinsey's own research ties balanced investment, not technology spend alone, to realized bottom-line impact.

## Watch-outs

- Skipping stages under executive pressure — attempting Gartner Level 4 systemic deployment while genuinely still at Level 1–2 awareness — is the most common and most expensive mistake; the frameworks exist to slow this impulse down with evidence
- Treating "AI strategy" as a document to write on day one, before any pilot experience exists, inverts Ng's own sequencing and tends to produce strategy disconnected from what AI can realistically do inside that organization
- Maturity models measure organizational capability, not the sophistication of any single AI model — a client can have access to the most advanced model available and still sit at Gartner Level 1 if there's no data governance, trained workforce, or integrated workflow around it
- McKinsey's six building blocks are explicitly interdependent — investing in one (usually technology/data, the easiest to procure) while neglecting the others (talent, operating model, adoption) is why many well-funded AI programs stall despite adequate technology
- These models describe organizational readiness, not whether a given AI capability should be built or bought — pair with [ai-build-vs-buy.md](ai-build-vs-buy.md) rather than treating maturity level alone as a build/buy signal

## Related

- [ai-build-vs-buy.md](../strategy/ai-build-vs-buy.md) — an organization's maturity stage directly bounds which build/buy default is realistic for it right now
- [crisp-dm-mlops.md](../strategy/crisp-dm-mlops.md) — once past Ng's pilot stage into anything resembling Extend/Evolve, CRISP-DM and MLOps are the process discipline that governs actual model delivery
- [ai-governance-nist-eu.md](../strategy/ai-governance-nist-eu.md) — governance maturity (risk management, compliance) is part of Gartner's later stages and McKinsey's operating-model building block, not a separate afterthought
- [okrs-execution.md](../people-org/okrs-execution.md) — sequencing an AI roadmap through these stages is itself an execution-discipline problem, well served by the same OKR cadence used for other cross-functional initiatives
