---
domain: strategy
concept: Balanced Scorecard
source: 'research — Kaplan, R.S. & Norton, D.P. (1992), "The Balanced Scorecard: Measures That Drive Performance," Harvard Business Review'
tags: [strategy-execution, kpis, perspectives, alignment]
---

# Balanced Scorecard

The Balanced Scorecard, introduced by Robert Kaplan and David Norton in a 1992 HBR article, was built to fix a specific failure mode they observed: companies managed almost entirely by financial metrics, which are lagging indicators that tell you what already happened and say nothing about whether the business is building the capability to keep succeeding. The Scorecard forces management to view performance through four linked perspectives simultaneously — financial, customer, internal process, and learning & growth — and, critically, to build explicit cause-and-effect chains (via a strategy map) connecting improvements in the non-financial perspectives to the financial outcomes leadership actually cares about. A consultant needs it because "we track KPIs" is not the same as "our KPIs are linked to strategy" — most client dashboards are a pile of metrics with no causal story connecting them, and the Balanced Scorecard is the discipline for building that story.

## When to use

- A client's strategy exists as a slide deck but has never been translated into metrics that managers and staff actually see and act on day to day.
- Leadership complains that "everyone hits their KPI targets but the company isn't achieving its strategy" — usually a sign of unlinked metrics, exactly the failure mode the Scorecard targets.
- A client is over-indexed on financial reporting (the CFO's dashboard is the only dashboard) and has no structured way to talk about customer, process, or capability health until financials already show the damage.
- Rolling a corporate strategy down into business-unit or team-level scorecards, so frontline execution stays connected to the top-level strategic intent instead of drifting into locally optimized but strategically disconnected metrics.
- Post-[mckinsey-7s.md](mckinsey-7s.md) alignment work, when Strategy and Structure have been reset and the client needs the measurement system (Systems) to actually reinforce the new direction rather than the old one.

## How it works

### The four perspectives

- **Financial** — the lagging, outcome-level perspective: revenue growth, profitability, return on capital, cost structure. Answers "how do we look to shareholders?" This is where traditional management reporting already lives, and the Scorecard doesn't discard it — it insists financial results be *explained* by the other three.
- **Customer** — market share, customer satisfaction, retention, acquisition, and the specific value proposition attributes that matter to the target segment (price, quality, time, function, service). Answers "how do customers see us?" This perspective is the causal link between internal execution and eventual financial results — you don't get financial results without first winning and keeping customers.
- **Internal Process** — the operational and innovation processes that must excel to deliver the customer value proposition: quality, cycle time, cost, new-product development pipeline, operational efficiency. Answers "what must we excel at internally?" This is where most operational KPIs already live, but the Scorecard requires naming *which* processes actually drive the customer perspective's targets, not tracking every process equally.
- **Learning & Growth** — the enabling perspective: employee capability and skills, information systems/technology, organizational culture and alignment, employee satisfaction and retention. Answers "can we continue to improve and create value?" This is the foundation — without the right people, systems, and culture, the internal processes can't improve, which means the customer perspective can't improve, which means financial results eventually stall.

### The causal chain and the Strategy Map

The four perspectives are not four independent scorecards — they're a hypothesized causal chain, typically read bottom-up: investments in **Learning & Growth** (better-trained staff, better systems) enable improvements in **Internal Process** (faster cycle time, higher quality), which improve the **Customer** perspective (better retention, higher satisfaction, new customer wins), which ultimately drive the **Financial** perspective (revenue growth, margin improvement). A **Strategy Map** is the visual tool for making this causal chain explicit: boxes for each objective, arranged by perspective, connected by arrows showing the hypothesized cause-effect links — e.g., "employee cross-training" (Learning & Growth) → "reduced order-processing errors" (Internal Process) → "improved customer satisfaction score" (Customer) → "increased repeat-purchase revenue" (Financial). The map is the artifact that turns a vague strategy statement into a testable set of hypotheses about what drives what.

### Building the Scorecard: the standard sequence

1. Translate the strategy into specific strategic objectives, one per perspective, that together tell the story of the strategy.
2. Draw the strategy map connecting objectives across perspectives with explicit cause-effect arrows.
3. For each objective, define one or more **measures** (the actual KPI) — a mix of lagging (outcome) and leading (driver) indicators.
4. Set **targets** for each measure over a defined time horizon.
5. Identify **initiatives** — the specific programs or projects that will move each measure toward its target.
6. Cascade the top-level Scorecard down into business-unit and team scorecards, each locally relevant but traceable back to the corporate strategy map.

## Example

**A B2B software company's simplified strategy map and scorecard:**

| Perspective | Strategic objective | Measure | Target | Initiative |
|---|---|---|---|---|
| Financial | Grow recurring revenue profitably | Net revenue retention | 115% within 12 months | — |
| Customer | Increase enterprise customer retention and expansion | Customer satisfaction (CSAT) score; expansion revenue rate | CSAT ≥ 4.5/5; 20% expansion rate | Dedicated customer success function |
| Internal Process | Reduce time-to-value for new customers | Average onboarding time | Cut from 45 to 20 days | Redesigned onboarding workflow; automated provisioning |
| Learning & Growth | Build customer success team capability | Certified customer success reps; internal tool adoption rate | 100% certified within 6 months; 90% adoption | New certification program; internal tooling rollout |

Read bottom-up: certifying customer success reps and rolling out better internal tooling (Learning & Growth) is hypothesized to cut onboarding time (Internal Process), which is hypothesized to raise CSAT and expansion revenue (Customer), which is hypothesized to raise net revenue retention (Financial). If net revenue retention doesn't move despite onboarding time falling, that's diagnostic information — either the Customer-to-Financial link is broken, or the Internal-Process-to-Customer link doesn't hold as assumed — rather than a mystery, because the causal chain was made explicit up front.

## Applying it for a client

Build the strategy map with the client's leadership team in the room, working top-down from the financial objective backward through customer, process, and capability — clients often want to start from whatever metrics they already have, which produces a scorecard that describes current operations rather than one that tests the strategy. Insist on a mix of leading and lagging measures per perspective; a scorecard built entirely from lagging financial-style metrics (percentage complete, revenue-to-date) just recreates the traditional dashboard the tool exists to fix. When cascading to business-unit level, require each unit's scorecard to trace at least one objective back to a corporate-level box on the strategy map — a unit scorecard with no visible link upward is a sign the unit is locally optimizing rather than executing the strategy. Revisit the causal arrows periodically as real data comes in: a Balanced Scorecard's map is a hypothesis, and part of the ongoing value is using actual results to confirm, refine, or discard specific cause-effect links rather than treating the first version as permanent.

## Watch-outs

- The most common implementation failure is treating the four perspectives as four independent lists of metrics rather than building the causal strategy map first — without the map, the Scorecard degenerates into "more KPIs," which is the exact problem it was designed to solve.
- Too many measures per perspective dilutes focus — Kaplan and Norton's own guidance is roughly 4-7 measures per perspective; a scorecard with 20 metrics in one box has stopped forcing prioritization, which is the tool's real discipline.
- A scorecard that's never revisited becomes stale — strategy maps encode hypotheses, and hypotheses need to be checked against actual results periodically, not treated as a one-time deliverable filed away after the workshop.
- Targets set without genuine baseline data invite gaming — a unit head incentivized against a target they had no part in setting, and no real baseline to validate, will optimize the measure rather than the underlying objective (Goodhart's Law risk is real here).
- The tool measures strategy execution — it does not evaluate whether the strategy itself is sound; a beautifully built scorecard for a flawed strategy just executes the flaw more efficiently. Validate the strategy (via [porters-five-forces.md](porters-five-forces.md), [porters-generic-strategies.md](porters-generic-strategies.md), or [blue-ocean-strategy.md](blue-ocean-strategy.md)) before building the scorecard that measures it.

## Related

- [mckinsey-7s.md](../strategy/mckinsey-7s.md) — the Systems element of 7S is where the Balanced Scorecard physically lives inside an organization's operating model.
- [product-roadmap.md](../product-management/product-roadmap.md) — initiatives on a strategy map often become roadmap items at the product level.
- [hr-management-and-planning.md](../operations/hr-management-and-planning.md) — Learning & Growth perspective objectives frequently translate into HR/L&D programs.
- [three-horizons-of-growth.md](../strategy/three-horizons-of-growth.md) — different time-horizon bets may need different scorecards, since an H3 bet's Financial perspective is deliberately not yet the primary success measure.
