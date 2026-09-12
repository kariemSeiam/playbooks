---
domain: finance
concept: Unit Economics (LTV, CAC & Payback)
source: research — David Skok (For Entrepreneurs), Bessemer Venture Partners "State of the Cloud", a16z
tags: [ltv, cac, unit-economics, saas, profitability]
---

# Unit Economics (LTV, CAC & Payback)

Unit economics measures whether a single customer is profitable to acquire and serve — strip away everything else about a company (market size, growth rate, team) and this is the number that determines whether the business model actually works. Popularized in its modern SaaS form by David Skok, it's the single best predictor of startup sustainability because a company can grow fast, raise well, and still die from unit economics that were broken from day one — growth just makes broken unit economics burn cash faster, not slower.

## When to use

- Before scaling any paid acquisition channel — know whether spending more actually compounds or just burns faster.
- In fundraising, when investors ask "why does this business work" — LTV:CAC and payback are the first numbers a competent investor checks.
- When comparing acquisition channels or customer segments against each other, not just the business as a blended average.
- When a client says "we're growing" but cash keeps getting tighter — unit economics usually explains the gap (see [burn-rate-runway.md](burn-rate-runway.md)).
- Before setting a board-level growth target — a growth number without a unit-economics constraint is just a burn target in disguise.

## How it works

### The three core numbers

**ARPU** — Average Revenue Per User/account, usually monthly (for SaaS, this is the same figure that rolls up into MRR — see [revenue-recognition-saas-metrics.md](revenue-recognition-saas-metrics.md)).

**LTV (Lifetime Value)** — the total gross profit a customer generates over the entire time they stay a customer.

```text
LTV = ARPU × Gross margin % × Average customer lifespan (months)
Average customer lifespan = 1 / Monthly churn rate
```

Using gross margin (not raw revenue) matters: LTV is meant to answer "how much profit does this customer generate," and a customer's revenue includes the cost of serving them (hosting, support, COGS). Revenue-only LTV overstates the number, sometimes by 20–30 points depending on the business.

**CAC (Customer Acquisition Cost)** — the fully-loaded cost to acquire one new paying customer.

```text
CAC = (Total sales + marketing spend in period) / New customers acquired in period
```

"Fully-loaded" is the load-bearing word: include sales salaries, commissions, marketing spend, tooling/ad platform costs — not just ad spend. Counting only ad spend is the most common way CAC gets understated.

**CAC Payback Period** — how many months it takes a customer's gross profit to repay their own acquisition cost.

```text
CAC Payback (months) = CAC / (ARPU × Gross margin %)
```

### The ratios and their targets

| Metric | Formula | Target | Notes |
|---|---|---|---|
| LTV:CAC ratio | LTV / CAC | ≥ 3:1 | David Skok's viability floor for a recurring-revenue business; top public SaaS companies run closer to 5:1 |
| CAC payback | CAC / (ARPU × margin) | < 12 months | Skok's textbook rule of thumb for SaaS |

**A real-world gap worth flagging to clients:** the "under 12 months" payback rule is more aggressive than what most companies actually post today. Benchmarkit's data across hundreds of SaaS companies shows median payback of ~11 months below $1M ARR, but climbing to ~16–18 months by the time a company reaches $5M–$50M ARR — payback tends to lengthen, not shorten, as a company scales and moves upmarket or adds more expensive enterprise sales motion. Use the 12-month figure as an efficiency bar to aim for, not as evidence something is broken if a scaling company is at 16.

**LTV:CAC can also be too high.** A ratio of 8:1 or 10:1+ doesn't mean "great business" by default — it often means the company is under-investing in growth relative to how profitable each customer is, leaving market share on the table that a faster-spending competitor will take. Treat 3:1–5:1 as the target band, not "higher is strictly better."

## Example

A vertical-SaaS company evaluating its paid-acquisition channel:

- ARPU = $200/month
- Gross margin = 75%
- Monthly churn = 3% → average customer lifespan = 1 / 0.03 = 33.3 months
- Fully-loaded CAC = $1,500 (from $450,000 in quarterly sales + marketing spend ÷ 300 new customers that quarter)

```text
LTV = 200 × 0.75 × 33.3 = $5,000
LTV:CAC = 5,000 / 1,500 = 3.33 : 1        → clears the 3:1 floor, but not by much
CAC Payback = 1,500 / (200 × 0.75) = 1,500 / 150 = 10 months   → under the 12-month bar
```

This company is viable but thin — a small increase in churn (say 3% → 4%, lifespan drops to 25 months) drags LTV down to $3,750 and the ratio to 2.5:1, below the floor. That sensitivity is the actual finding to bring to the client, not the point estimate.

## Applying it for a client

Compute LTV:CAC and payback **per channel and per segment**, never just as one blended company-wide number — a blended 3.5:1 routinely hides one channel at 6:1 (stop starving it) and another at 1.2:1 (stop funding it). Get the real fully-loaded CAC by asking for the actual sales/marketing headcount and spend, not the number the client first offers — founders systematically undercount CAC by excluding sales salaries and tools. Then stress-test the churn assumption specifically: because average lifespan is `1/churn`, LTV is extremely sensitive to small churn changes, and that sensitivity is usually the single most useful thing to show a client before they scale a channel further.

## Watch-outs

- `1/churn` for average lifespan assumes constant (exponential-decay) churn — real cohorts rarely decay that cleanly. For any material decision, build the actual cohort retention curve instead of trusting the shortcut (see [startup-financial-modeling.md](startup-financial-modeling.md)).
- LTV built on revenue instead of gross margin overstates true customer profitability — always confirm which one a client's reported LTV actually uses.
- Blended CAC across all channels hides the fact that one channel may be subsidizing another; segment before deciding where to spend more.
- A very high LTV:CAC (8:1+) is not automatically good — it can signal under-investment in growth, not unusual efficiency.
- CAC payback benchmarks drift longer as a company moves upmarket (bigger deals, longer sales cycles) — don't flag a rising payback period as automatically alarming without checking whether ACV and deal complexity also rose.

## Related

- [burn-rate-runway.md](../finance/burn-rate-runway.md) — bad unit economics is usually the underlying reason a "growing" company is burning through runway.
- [revenue-recognition-saas-metrics.md](../finance/revenue-recognition-saas-metrics.md) — ARPU/MRR feed unit economics directly; NRR and GRR extend the same "what is this customer base actually worth" question forward in time.
- [startup-financial-modeling.md](../finance/startup-financial-modeling.md) — cohort retention curves are the rigorous version of the `1/churn` lifespan shortcut used here.
- [valuation-methods.md](../finance/valuation-methods.md) — LTV and CAC payback are exactly the inputs an investor checks before trusting a growth-based valuation.
