---
domain: finance
concept: Startup Financial Modeling (3-Statement, Driver-Based, Cohort & Scenario)
source: research — Corporate Finance Institute (CFI); standard VC/PE modeling practice
tags: [financial-model, projections, scenarios, cohort, driver-based]
---

# Startup Financial Modeling (3-Statement, Driver-Based, Cohort & Scenario)

A financial model is a working simulation of the business, not a set of typed-in guesses about future revenue. Done properly, it links the income statement, balance sheet, and cash flow statement so that a single assumption change (headcount, churn, sales cycle length) flows through all three automatically, builds revenue bottom-up from cohort retention data rather than a blended growth rate, and produces base/bull/bear scenarios by toggling the same driver assumptions rather than rebuilding formulas. It's the tool that turns "we think we'll grow 3x next year" into a defensible, testable plan.

## When to use

- Any fundraise — investors expect the three statements to actually tie together, not a revenue tab floating disconnected from cash and headcount.
- Board planning and budget-vs-actual reviews, where the model needs to answer "what if" questions live in the room, not after a week of rebuilding.
- Before a major decision with multi-quarter cash consequences — a new hiring plan, a pricing change, entering a new market.
- Any time [burn-rate-runway.md](burn-rate-runway.md)'s runway number needs to be stress-tested against a plan, not just extrapolated from last month.

## How it works

### The 3-statement linkage

The three statements aren't three separate tabs — they're one model viewed three ways:

- **Income statement** produces net income for the period (see [income-statement-vs-balance-sheet.md](income-statement-vs-balance-sheet.md)).
- **Balance sheet** rolls net income into retained earnings, and every other line (AR, AP, debt, cash) updates from the period's activity.
- **Cash flow statement** starts from the income statement's net income and reconciles it to the balance sheet's actual cash movement (see [cash-flow.md](cash-flow.md)).

If a driver assumption changes — say, a delayed hire — headcount cost drops on the income statement, cash preserved shows up on the cash flow statement, and the balance sheet's cash balance updates accordingly. If the three don't move together automatically, the model isn't actually linked; it's three spreadsheets that happen to sit near each other.

### Driver-based assumptions, not hardcoded growth rates

The weak version of a model says "revenue grows 20% per quarter." The driver-based version builds revenue from the actual operating levers that produce it:

```
Revenue = New customers/month (driver) × ARPU (driver) × Retention curve (driver)
New customers/month = Sales reps × Quota attainment % × Deals per rep (drivers)
```

Changing a driver — hiring plan slips a quarter, conversion rate improves 2 points — recalculates revenue, and because the model is linked, recalculates cash and headcount cost with it. This is what makes the model useful for real decisions instead of just producing a number to defend.

### Cohort retention modeling

Blended, company-wide churn (the `1/churn` shortcut used in [unit-economics.md](unit-economics.md)) hides whether new cohorts are retaining better or worse than old ones — exactly the kind of shift that matters most and shows up latest in a blended number. Cohort modeling instead tracks, for each acquisition month, what fraction of that cohort is still active N months later, and builds total revenue as the sum across all live cohorts.

### Scenario analysis

Build **Base** (most likely trajectory), **Bull** (a named upside driver improves — faster sales cycle, higher conversion, lower churn), and **Bear** (a named downside driver worsens — CAC rises, churn increases, a hire slips) by changing the specific driver cells that represent those risks — never by applying a blanket "×1.2 / ×0.8" to the base case's output. A scenario has to name *which* driver breaks and by how much, or it's not actually testing anything.

## Example

**Cohort revenue build.** Three monthly cohorts of a subscription product, ARPU = $100/month, with a stabilizing retention curve: month 0 = 100%, month 1 = 90%, month 2 = 85%.

| Cohort | Size | Age in March | Retention | Active | MRR |
|---|---|---|---|---|---|
| January | 100 | 2 months | 85% | 85 | $8,500 |
| February | 120 | 1 month | 90% | 108 | $10,800 |
| March | 140 | 0 months | 100% | 140 | $14,000 |
| **Total March MRR** | | | | | **$33,300** |

**Bear-case retention shock.** Same cohorts, but retention runs 5 points worse across the board (month 1 = 85%, month 2 = 80%):

```
January (age 2, 80%): 100 × 0.80 = 80 active  → $8,000
February (age 1, 85%): 120 × 0.85 = 102 active → $10,200
March (age 0, 100%): 140 active                → $14,000
Bear-case March MRR = $32,200  (vs. $33,300 base — a 3.3% miss)
```

A 3.3% miss at month 3 looks small. But because retention curves compound, the same 5-point degradation widens dramatically by month 12+ as more cohorts age through the worse curve — this is precisely the failure mode a blended-churn model hides until the damage is already large and a cohort-level model catches immediately. Always run this comparison before telling a client "a small retention dip isn't a big deal."

## Applying it for a client

Interview for the real drivers before opening a spreadsheet: sales cycle length, average deal size by segment, hiring plan by role and start date, and — critically — the retention curve broken out by cohort or segment, not one blended number. Structure the model on a rolling 18–24 month horizon so it always reaches past the next fundraise milestone. Wire the model's outputs directly into the other tools in this stack: unit economics ([unit-economics.md](unit-economics.md)) and runway ([burn-rate-runway.md](burn-rate-runway.md)) should read off the same driver cells as the 3-statement model, not be computed separately and reconciled by hand later — divergence between "the model" and "the unit economics slide" is one of the fastest ways a client loses credibility with investors. For a true pre-seed client with no operating data yet, don't over-build: use top-down/bottom-up sanity bands on 2–3 key drivers rather than a 12-tab model resting on assumptions nobody can defend.

## Watch-outs

- Circular references (cash balance affects interest income/expense, which affects net income, which affects cash) are common in a real 3-statement model — resolve with an iterative calculation setting or a debt/cash "plug" schedule, don't just break the link to make the error go away.
- A model with too many tabs and too much false precision is worse than a simple one for a pre-revenue company — there's no data yet to make granular assumptions defensible.
- A "bear case" that's just the base case multiplied by a flat factor isn't a scenario — it has to name the specific driver that breaks (churn, sales cycle, CAC) and move only that one.
- Models rot fast. Without a monthly actual-vs-model variance review, a model that was accurate at the fundraise is fiction by month four — schedule the review cadence when the model is built, not after it's already stale.
- Revenue built from a single blended churn number will look fine right up until it doesn't — always sanity-check the blended assumption against at least a rough cohort breakdown.

## Related

- [unit-economics.md](../finance/unit-economics.md) — LTV's `1/churn` shortcut is the simplified version of the cohort retention curve modeled here in full.
- [burn-rate-runway.md](../finance/burn-rate-runway.md) — runway and burn multiple should be read directly off this model's driver assumptions, not computed separately.
- [cash-flow.md](../finance/cash-flow.md) and [income-statement-vs-balance-sheet.md](../finance/income-statement-vs-balance-sheet.md) — the two other statements this model links to the income statement.
- [valuation-methods.md](../finance/valuation-methods.md) — DCF valuation is only as credible as the projections this model produces.
