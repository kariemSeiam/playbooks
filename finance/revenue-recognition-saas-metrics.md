---
domain: finance
concept: Revenue Recognition (ASC 606/IFRS 15) & SaaS Recurring-Revenue Metrics
source: research — FASB ASC 606 / IASB IFRS 15 (converged standard, effective 2018); SaaS Capital, ChurnZero industry benchmarks
tags: [revenue, mrr, arr, nrr, accounting, saas]
---

# Revenue Recognition (ASC 606/IFRS 15) & SaaS Recurring-Revenue Metrics

ASC 606 (US GAAP) and IFRS 15 (international) are the converged accounting standard that governs *when* a company is allowed to book revenue — and for a subscription business, when cash is collected and when revenue is recognized are routinely two very different months. On top of that accounting layer sit the operating metrics — MRR, ARR, NRR, GRR — that tell a SaaS business (and its investors) whether the recurring-revenue base is actually healthy, growing, or quietly leaking underneath a headline number that still looks fine.

## When to use

- Any time a SaaS client collects cash upfront (annual prepay) and needs to know how much of it is actually recognizable revenue this month, not just deferred on the balance sheet.
- Before external financing, an audit, or acquisition due diligence — cash-basis "revenue" gets restated under ASC 606/IFRS 15 in a QoE (quality of earnings) review, and it can materially shrink the reported top line if it wasn't done correctly from the start.
- Any monthly/board reporting cycle for a subscription business — MRR movement (new, expansion, contraction, churn) and NRR/GRR are the standing health dashboard.
- Whenever a client's growth story rests heavily on "upsells" — GRR alongside NRR is how you check whether the *existing* customer base is actually shrinking underneath the expansion revenue.

## How it works

### The five-step revenue recognition model (ASC 606 / IFRS 15)

1. **Identify the contract** with the customer.
2. **Identify the performance obligations** in the contract — the distinct promises to deliver goods or services.
3. **Determine the transaction price** — the total consideration the company expects to be entitled to.
4. **Allocate the transaction price** across the performance obligations, based on each one's standalone selling price.
5. **Recognize revenue** as (or when) each performance obligation is actually satisfied.

The core principle: revenue is recognized as value is delivered to the customer, not when cash changes hands.

### SaaS recurring-revenue metrics

```text
MRR = Monthly Recurring Revenue — all active subscriptions normalized to a monthly value
ARR = MRR × 12
Net New MRR = New MRR + Expansion MRR − Contraction MRR − Churned MRR
```

```text
NRR (Net Revenue Retention) = (Starting MRR + Expansion − Contraction − Churn) / Starting MRR
GRR (Gross Revenue Retention) = (Starting ARR − Churn − Contraction) / Starting ARR
```

Both are measured over a trailing period (usually 12 months) on an *existing customer cohort* — new-customer revenue is deliberately excluded from both, because the question they answer is "how much of what we already had did we keep and grow," not "how much did we sell this year."

**Benchmarks:**

| Metric | Band | Read |
|---|---|---|
| NRR | > 130% | Best-in-class |
| NRR | 100–120% | Good |
| NRR | < 100% | Concerning — losing more than you expand |
| GRR | ~90%+ | Healthy churn/contraction discipline |
| GRR | Can never exceed 100% | If it does, expansion has been miscounted into it |

NRR varies by segment: enterprise (large ACV) SaaS commonly runs 118–150%; mid-market ~108%; SMB-focused products often sit closer to 97–115% due to naturally higher logo churn.

## Example

**Revenue recognition, worked.** A company sells a 1-year SaaS subscription for $12,000, paid upfront in cash on January 1, plus a distinct one-time $2,000 onboarding/implementation service delivered in January.

- Step 2: two distinct performance obligations — the subscription (delivered ratably over 12 months) and the onboarding service (delivered at a point in time).
- Step 3: total transaction price = $14,000.
- Step 4: allocate — $2,000 to onboarding (standalone service), $12,000 to the subscription.
- Step 5: recognize $2,000 immediately on completion of onboarding; recognize the $12,000 subscription ratably at $1,000/month for 12 months.

Cash received January 1 is $14,000, but January's recognized revenue is $2,000 (onboarding) + $1,000 (month 1 of subscription) = **$3,000** — the remaining $11,000 sits on the balance sheet as deferred revenue (a liability) until it's earned in future months. Recognizing the full $14,000 in January would overstate revenue by $11,000 and is a common early-stage bookkeeping error that has to be restated before any real audit or fundraise.

**NRR/GRR, worked.** A cohort of existing customers starts a trailing-12-month period at $100,000 MRR. Over the period: $8,000 lost to churn, $4,000 lost to contraction (downgrades), $25,000 gained from expansion (upsells within the same customers).

```text
NRR = (100,000 − 8,000 − 4,000 + 25,000) / 100,000 = 113,000 / 100,000 = 113%
GRR = (100,000 − 8,000 − 4,000) / 100,000 = 88,000 / 100,000 = 88%
```

NRR at 113% lands comfortably in the "good" band — the headline looks healthy. But GRR at 88% is below the ~90% healthy threshold: **excluding expansion, the base is actually shrinking.** The strong NRR is being carried entirely by upsell revenue on a shrinking set of retained logos — a distinction worth flagging to a client even though the top-line NRR number alone reads as fine.

## Applying it for a client

Always compute GRR alongside NRR — never present NRR on its own, because a client (or their own board deck) can hide real churn behind strong expansion, and the gap between the two numbers is exactly where that's happening. Get finance to actually apply the five-step model rather than recognizing on a cash basis, especially before any external financing or M&A process — the earlier this is fixed, the less painful the eventual restatement. Use MRR *movement* (new/expansion/contraction/churn), not just the ending MRR figure, as the standing monthly dashboard — the components show where the business is winning or leaking, which the net number alone can't.

## Watch-outs

- Recognizing a full annual prepay as revenue in month one is the most common early-stage rev-rec error — it will need restating before a real audit, and it inflates every metric downstream (growth rate, margin, valuation multiples).
- NRR calculated logo-weighted instead of dollar-weighted gives a materially different, less useful answer — always dollar-weight.
- GRR can never mathematically exceed 100%; if a client's number does, expansion revenue has been miscounted into what should be a pure retention/churn measure.
- Multi-year contracts with built-in price escalators need the escalation modeled into the performance-obligation allocation over time, not recognized as a step-function jump.
- A strong blended NRR can mask a shrinking core base if it's being carried by expansion on a small number of accounts — always check concentration (how many logos are driving the expansion) alongside GRR.

## Related

- [unit-economics.md](../finance/unit-economics.md) — ARPU and churn feed directly into LTV; NRR/GRR are the forward-looking, cohort-level extension of the same retention question.
- [startup-financial-modeling.md](../finance/startup-financial-modeling.md) — MRR movement and cohort retention curves are exactly what a driver-based revenue build should be modeling.
- [cash-flow.md](../finance/cash-flow.md) and [income-statement-vs-balance-sheet.md](../finance/income-statement-vs-balance-sheet.md) — deferred revenue from upfront cash collection is a balance-sheet liability, not income-statement revenue, until it's earned.
