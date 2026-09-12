---
domain: sales-and-bizdev
concept: BANT and SPICED
source: research — IBM sales training (BANT, mid-20th century origin); Winning by Design (SPICED, recurring-revenue qualification)
tags: [qualification, budget, authority, recurring-revenue, lifecycle]
---

# BANT and SPICED

BANT (Budget, Authority, Need, Timeline) and SPICED (Situation, Pain, Impact, Critical event, Decision) are both lightweight qualification filters, but built for different eras and motions: BANT for a quick go/no-go on a lead in a transactional or one-time-purchase sale, SPICED for a recurring-revenue B2B motion where the same qualification needs to travel with the account from first sale through renewal. A consultant needs both because reaching for full MEDDPICC on every inbound lead is overkill — most orgs need a fast filter at the top of the funnel and a fuller framework only once a deal is worth the qualification effort, and getting that filter wrong (using an outdated one, or using none at all) is one of the most common reasons SDR/BDR teams pass bad leads to AEs.

## When to use

- **BANT**: a 2–5 minute SDR/BDR triage call or an inbound MQL-to-SQL handoff, where the goal is a fast signal on whether to route the lead to an AE at all — especially for transactional or one-time-purchase-shaped deals.
- **SPICED**: subscription/recurring-revenue B2B (SaaS especially), account-based motions where the qualification needs to be shared language across AE, CS, and renewal teams, or PLG-to-sales-assist handoffs.
- Either, as a lighter-weight complement to MEDDPICC/MEDDPICC when a full qualification exercise isn't yet justified by deal size.
- Designing CRM lead-scoring rules and routing logic — both frameworks map cleanly onto required-field gates before a lead can advance stage.

## How it works

### BANT — Budget, Authority, Need, Timeline

Created by IBM's sales organization (an origin dating to the mid-20th century, from an era of one-time capital-equipment sales), BANT asks four questions in whatever order best fits the conversation — many orgs re-order to Need-Authority-Budget-Timeline so a cold inbound call doesn't open by asking about money before rapport and relevance are established.

| Letter | Question | Purpose |
|---|---|---|
| Budget | Does the prospect have, or can they get, money allocated for this category of purchase? | Filters out leads with no realistic path to spend. |
| Authority | Are we talking to someone who decides or meaningfully influences the decision? | Prevents a rep from investing a full cycle in someone who can't move the deal. |
| Need | Is there an actual business need matching what's being sold? | Basic fit check — is this even the right product for this prospect? |
| Timeline | Is there an active timeframe or trigger driving urgency? | Distinguishes "interested eventually" from "buying this quarter." |

BANT's core weakness is baked into its origin: it assumes budget is a fixed, pre-allocated pool (true for one-time capital purchases, less true for software where "budget" is often created after value is proven) and treats "Timeline" as a vague window rather than a specific triggering event.

### SPICED — Situation, Pain, Impact, Critical event, Decision

Built by Winning by Design (a B2B SaaS revenue-architecture consultancy) specifically for recurring-revenue motions, SPICED is designed to be used continuously across the customer lifecycle — not just at initial qualification, but again at renewal and expansion — so AE and Customer Success teams share one qualification vocabulary instead of re-discovering the account from scratch at each stage.

| Letter | Element | What it captures |
|---|---|---|
| Situation | Current state — systems, team, process in place today | Same role as SPIN's Situation questions: grounding facts, not yet a problem. |
| Pain | The specific business friction actually costing the prospect something | An implicit-need-level problem statement. |
| Impact | The quantified cost of the pain if unresolved, and quantified value of resolving it | Plays the same role as MEDDIC's Metrics — the ROI number that justifies spend, re-measurable post-sale with real usage data. |
| Critical event | A forcing function or deadline that makes *now* the moment to act — a compliance deadline, a contract renewal, a funding round, a market shift | A sharper, more falsifiable version of BANT's "Timeline." |
| Decision | Who is involved and what process they'll use to decide | A lighter merge of BANT's Authority with MEDDIC's Decision Criteria/Process. |

Because "Critical Event" and "Impact" are designed to be re-measured at renewal (a new critical event — the renewal date itself — recurs naturally, and Impact can now be checked against actual usage data instead of a projection), SPICED is built to travel from AE to CS without translation.

## Example

**BANT, SDR call:** An SDR at a mid-market payroll-software company gets an inbound demo request from an HR manager. Budget — "Do you have budget allocated for a payroll platform this year, or would this be a new line item?" Authority — "Who else is typically involved in choosing a system like this?" Need — "What's driving the search — problem with your current provider, or a new requirement?" Timeline — "Is there a date this needs to be live by (open enrollment, fiscal year)?" Four minutes in, the SDR has enough to route (or not route) to an AE.

**SPICED, AE call:** An AE at a subscription analytics platform is 90 days from a customer's renewal and wants to build an expansion case. Situation — current usage across three teams. Pain — one team routinely exports data to a separate BI tool because a dashboard they need doesn't exist in-product. Impact — quantifies the manual export/rebuild time at roughly 6 hours/week across the team, and the risk that a poor renewal experience could shrink the account rather than expand it. Critical event — the renewal itself, 90 days out, which the AE ties to a proposal for an add-on module rather than treating renewal and expansion as separate conversations. Decision — the same procurement contact who signed originally, but now with a new budget-holder (a VP who inherited the team) who needs to be looped in before the renewal date.

## Applying it for a client

Embed BANT directly into SDR call scripts and CRM lead-routing rules as the MQL-to-SQL gate — it should be a fast filter, not a deep qualification exercise, and "no budget yet" should route to nurture, not disqualify, since software budget is often created once value is demonstrated. Embed SPICED as the shared qualification language across the whole revenue org for recurring-revenue clients, so the fields an AE captures at the original sale are the same fields CS references at renewal — this alone often eliminates the re-discovery work that makes renewals feel like starting over. For a client selling both a low-touch self-serve tier and a higher-touch enterprise tier, expect to run BANT for the former and SPICED (or full MEDDPICC) for the latter — matching qualification weight to deal weight is itself a design decision worth making explicit, not defaulting to one framework everywhere.

## Watch-outs

- BANT's rigid "no budget = disqualify" rule kills real inbound interest too early in software motions — treat Budget as "can this org create budget for this," not "does a budget line already exist."
- BANT alone under-qualifies anything beyond a simple, single-stakeholder sale — once a deal graduates past initial SDR triage into a multi-stakeholder enterprise cycle, layer MEDDPICC on top ([meddic-meddpicc.md](meddic-meddpicc.md)) rather than relying on BANT for the whole cycle.
- SPICED is a vendor-originated framework (Winning by Design's own consulting methodology) rather than an independently research-validated model like SPIN — treat it as emerging-but-credible, useful and widely adopted in SaaS, but not evidence-backed at the level of Rackham's 35,000-call study.
- Either framework is only as trustworthy as what's actually entered in CRM — stale qualification fields nobody updates after the first call are worse than no framework at all, because they create false forecast confidence (see [sales-pipeline-revops.md](sales-pipeline-revops.md)).

## Related

- [meddic-meddpicc.md](../sales-and-bizdev/meddic-meddpicc.md) — the heavier framework to layer on once a deal passes initial BANT/SPICED triage and enters a complex, multi-stakeholder cycle.
- [spin-selling.md](../sales-and-bizdev/spin-selling.md) — SPICED's Situation and Pain stages borrow directly from SPIN's questioning categories.
- [sales-pipeline-revops.md](../sales-and-bizdev/sales-pipeline-revops.md) — where BANT/SPICED fields live operationally as CRM stage-gate criteria and lead-routing SLAs.
