---
domain: strategy
concept: GE-McKinsey Nine-Box Matrix
source: research — developed by McKinsey & Company for General Electric in the early 1970s; documented in Hax, A.C. & Majluf, N.S. (1983), "The Use of the Industry Attractiveness-Business Strength Matrix in Strategic Planning," Interfaces
tags: [portfolio, prioritization, investment, business-units]
---

# GE-McKinsey Nine-Box Matrix

The Nine-Box Matrix was developed by McKinsey & Company for General Electric in the early 1970s, explicitly as a response to the limitations GE found in the BCG Growth-Share Matrix: reducing every business unit's position to two variables (market growth and relative share) felt too crude for a conglomerate as diverse as GE, whose units competed under very different conditions that a single growth-rate and share number couldn't capture. The Nine-Box replaces BCG's two single metrics with two *composite, multi-factor* scores — industry attractiveness and business unit strength — each built from several weighted criteria, plotted on a 3x3 (nine-cell) grid instead of BCG's 2x2. A consultant needs it whenever a client's portfolio decision requires more nuance than growth-rate-and-share alone can honestly provide — which is most real portfolios.

## When to use

- A client's units compete in industries where market growth rate alone is a poor proxy for attractiveness (e.g., a mature but highly profitable niche, or a fast-growing but brutally competitive one) — situations where BCG's two single variables would mislabel the unit.
- A client wants the resource-allocation conversation from [bcg-growth-share-matrix.md](bcg-growth-share-matrix.md) but pushes back that "market share isn't the only thing that matters" — the Nine-Box is the direct answer, letting the client weight the criteria that matter to their specific business.
- Post-BCG follow-up: after a first-pass BCG plot flags ambiguous cases (a Question Mark that might really be more attractive than the label suggests), the Nine-Box adds the nuance to make a confident call.
- Capital budgeting across a diversified portfolio where the board needs a defensible, multi-criteria rationale for why unit A gets more investment than unit B — a single growth number is an easy target for a unit head to argue against; a documented multi-factor score is harder to dismiss.

## How it works

### The two composite axes

**Industry Attractiveness** (vertical) — a weighted composite score built from criteria such as: market size and growth rate, industry profitability and margin structure, competitive intensity (informed by [porters-five-forces.md](porters-five-forces.md)), pricing trends, barriers to entry, technology/capital requirements, and macro/regulatory factors (informed by [pestel-analysis.md](../marketing/pestel-analysis.md)). Each criterion is scored (e.g., 1–5) and weighted by relative importance to produce a single composite attractiveness score, then bucketed into High / Medium / Low.

**Business Unit Strength** (horizontal) — a weighted composite score built from criteria such as: relative market share, brand strength and reputation, cost position relative to competitors, product/service quality, distribution reach, technology or IP position, and management/talent depth. Same scoring-and-weighting method, bucketed into High / Medium / Low.

### The grid and its zones

Crossing 3x3 buckets produces nine cells, which collapse into three strategic zones:

| | High Strength | Medium Strength | Low Strength |
|---|---|---|---|
| **High Attractiveness** | Invest/Grow | Invest/Grow | Selectivity |
| **Medium Attractiveness** | Invest/Grow | Selectivity | Harvest/Divest |
| **Low Attractiveness** | Selectivity | Harvest/Divest | Harvest/Divest |

- **Invest/Grow** (top-left cluster) — strong units in attractive industries. Prioritize capital, protect and extend the position, this is where the portfolio's future returns should concentrate.
- **Selectivity** (diagonal middle band) — mixed signals: either a strong unit in a middling industry, a middling unit in an attractive industry, or a genuinely middling unit in a middling industry. Requires case-by-case judgment rather than a default rule — invest selectively where a specific sub-segment or capability upgrade could shift the unit into the Invest/Grow zone, otherwise hold at maintenance-level investment.
- **Harvest/Divest** (bottom-right cluster) — weak units in unattractive industries. Minimize further investment, extract remaining cash, and plan for divestment or wind-down unless there's a specific strategic reason (e.g., a defensive necessity) to hold on.

Bubble size on the plotted chart typically represents the unit's market size, and a pie-slice within the bubble often shows the unit's share of that market — giving a third and fourth dimension of information beyond the x/y position.

### Why multi-factor beats two single metrics

The core methodological advance over BCG is that "attractiveness" and "strength" are judgment calls informed by multiple weighted inputs rather than a single hard number — this lets the analysis reflect industry-specific realities (a niche industry with modest growth but very high margins and few competitors can score High Attractiveness despite failing BCG's growth-rate test) and lets the client's own strategic priorities show up explicitly in the weighting scheme, rather than being hidden inside an assumed threshold.

## Example

**A diversified industrial conglomerate scoring three business units:**

| Unit | Industry Attractiveness factors | Score | Business Strength factors | Score | Zone |
|---|---|---|---|---|---|
| Precision components division | Moderate growth (6%), high margins, few qualified competitors due to certification barriers, stable long-term contracts | High | #1 market share, proprietary certifications, long customer relationships | High | **Invest/Grow** |
| Industrial software unit | High growth (18%), but intensifying competition from well-funded software entrants, uncertain long-term margin structure | Medium | New entrant, small share, but strong underlying engineering talent and an emerging platform advantage | Medium | **Selectivity** |
| Legacy fasteners division | Flat/declining commodity market, thin margins, many undifferentiated competitors | Low | Mid-tier share, aging plant, no cost advantage | Low | **Harvest/Divest** |

Where a plain BCG plot might have shown the industrial software unit as a Star (high growth, and if share happened to look decent by some measure) or Question Mark, the Nine-Box's composite Business Strength score — capturing that the unit is genuinely early-stage against better-funded rivals — moves it into Selectivity: a case for continued but disciplined, milestone-gated investment rather than an automatic "fund it, it's growing" conclusion. The precision components division, which a pure growth-rate lens might underrate (6% growth looks unremarkable next to the software unit's 18%), scores High Attractiveness once margin structure and entry barriers are weighted in — correctly flagging it as the portfolio's actual core investment priority.

## Applying it for a client

Build the weighting scheme collaboratively with the client's leadership team before scoring anything — the choice of which criteria matter and how heavily (is barrier-to-entry weighted as much as growth rate? is talent depth weighted as much as market share?) is itself a strategic statement, and a consultant who imposes a generic weighting scheme will get pushback later when a unit head disputes their score. Score each unit with the same rigor and the same named sources (industry reports for attractiveness criteria, competitive benchmarking for strength criteria) so the exercise survives scrutiny — a client sponsor's gut-feel score for their own favored unit is exactly the bias this more elaborate matrix exists to check. Once plotted, use the zone as a starting recommendation, not a final verdict, especially in the Selectivity band — that's where the real consulting judgment is earned, distinguishing a unit worth a targeted bet from one that's just occupying capital indefinitely in the middle of the chart. Pair the output with a phased capital plan: Invest/Grow gets multi-year committed capital, Selectivity gets milestone-gated tranches, Harvest/Divest gets a wind-down or sale timeline with an explicit decision date.

## Watch-outs

- The composite-score method is more defensible than BCG's two raw metrics, but it's also more subjective — the weighting and scoring can be gamed (consciously or not) by whoever runs the exercise to produce a pre-determined conclusion; document the criteria and weights before scoring, not after seeing where units land.
- Nine cells collapsing into three zones can hide meaningful differences — a unit at the border of Invest/Grow and Selectivity is a different conversation than one deep in either zone; report the underlying composite scores, not just the zone label.
- Like BCG, this is a portfolio-level tool — it doesn't replace unit-level strategy work ([porters-generic-strategies.md](porters-generic-strategies.md), [vrio-framework.md](vrio-framework.md)) on how a given unit should actually compete once its investment priority is set.
- Business Unit Strength criteria (brand, talent, cost position) are more qualitative than BCG's relative-market-share number — resist the temptation to average subjective 1–5 ratings into false precision; a composite "3.4" score should still be explainable in plain language to a skeptical board member.
- The tool assumes the client can meaningfully separate "industry attractiveness" from "our performance in it" — for a client with only one dominant business line, there's often not enough portfolio variation to make a nine-box exercise worthwhile; it earns its complexity in genuinely diversified portfolios.

## Related

- [bcg-growth-share-matrix.md](../strategy/bcg-growth-share-matrix.md) — the simpler two-variable predecessor this tool was built to improve on.
- [porters-five-forces.md](../strategy/porters-five-forces.md) — a primary input into the Industry Attractiveness score.
- [pestel-analysis.md](../marketing/pestel-analysis.md) — macro factors feeding the Industry Attractiveness score.
- [vrio-framework.md](../strategy/vrio-framework.md) — deeper resource-level test once a unit is confirmed as an Invest/Grow priority.
