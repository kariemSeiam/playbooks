---
domain: finance
concept: Burn Rate, Runway & Burn Multiple
source: research — Paul Graham ("Default Alive or Default Dead?", 2015); David Sacks (Burn Multiple, Craft Ventures)
tags: [burn, runway, cash, capital-efficiency, fundraising]
---

# Burn Rate, Runway & Burn Multiple

Burn rate is how fast a company spends its cash; runway is how long the cash on hand lasts at that rate; burn multiple is how much cash it costs to generate each dollar of new recurring revenue. Together they answer the three questions every board and every founder should be able to answer cold: how much are we spending, how long do we have, and is the spending actually buying growth or just going up in smoke. Paul Graham's "default alive vs. default dead" framing and David Sacks's burn multiple turned these from vague board-meeting anxieties into numbers you can compute and act on.

## When to use

- Every board meeting and monthly close — this is the standing capital-efficiency dashboard, not a one-time calculation.
- Before deciding whether/when to raise — the decision should be made with 6+ months of runway left, never at 2–3 months.
- When comparing two growth strategies (e.g., paid acquisition vs. sales-led) for capital efficiency, not just top-line growth.
- Any time a founder says "we're growing" — check whether growth is coming cheap (low burn multiple) or being bought at an unsustainable cost.

## How it works

### Gross burn vs. net burn vs. runway

```text
Gross burn  = total monthly cash operating expenses (before revenue)
Net burn    = Gross burn − Monthly cash revenue collected
Runway (months) = Cash on hand / Net burn
```

Target runway **18–24 months immediately post-raise** — long enough to hit the milestones needed for the next round without fundraising from a position of weakness in the final quarter of a raise.

### The Default Alive / Default Dead test (Paul Graham)

The question: *if current expenses stay flat and current revenue growth rate continues unchanged, does the company reach profitability before the cash on hand runs out?* If yes, it's **default alive** — it survives without raising again. If no, it's **default dead** — it needs a real change (raise, cut costs, or grow faster) or it fails, regardless of how good the story sounds in the room.

**How to run it:** take four inputs — current monthly expenses, current monthly revenue, the recent monthly revenue growth rate, and cash on hand — and project revenue forward at the current growth rate against flat expenses, month by month, tracking cumulative burn against the cash balance.

### Burn multiple (David Sacks)

```text
Burn Multiple = Net burn in period / Net new ARR in period
```

Net new ARR = the change in annualized recurring revenue over the period (new logos + expansion − churn − contraction). Lower is better: it answers "how many dollars did we burn to add one dollar of annual recurring revenue."

**Benchmark bands by stage:**

| Stage (ARR) | Typical | Target |
|---|---|---|
| Pre-seed–Seed ($0–1M) | 2.0–3.0 | < 2.0 once there's consistent pull |
| Seed–Early A ($1–3M) | 1.5–2.0 | 1.3–1.6 |
| Series A ($3–8M) | 1.0–1.5 | ~1.2 |
| Series B ($8–15M) | 0.8–1.2 | ~1.0 |
| Series C+ ($15M+) | 0.5–1.0 | 0.6–0.8 |

Elite is under 1.0 at Series A/B and under 0.7 at Series C+. Anything drifting past 2.0–3.0 at Series A or later is a real efficiency problem, not just an "investment year."

## Example

**Gross/net burn and runway.** Cash in bank: $3,000,000. Monthly cash revenue: $150,000. Monthly operating expenses: $400,000.

```text
Gross burn = $400,000/month
Net burn   = $400,000 − $150,000 = $250,000/month
Runway     = $3,000,000 / $250,000 = 12 months
```

Twelve months is under the 18–24 month target — this company needs to be actively fundraising now, not in six months.

**Burn multiple.** Same company: ARR was $1.2M at the start of the quarter and $1.8M at the end (net new ARR = $600,000 for the quarter). Quarterly net burn = $250,000 × 3 = $750,000.

```text
Burn Multiple = 750,000 / 600,000 = 1.25
```

1.25 sits inside the "target ~1.2" band for a company at this ARR range — capital-efficient growth, even though runway itself (above) is tight. This is exactly the kind of split signal a board needs both numbers to catch: efficient growth, but not enough cash cushion.

**Default alive / dead projection.** A different company: expenses flat at $400,000/month, current revenue $200,000/month growing 8%/month, $2,000,000 cash on hand.

| Month | Revenue | Net burn | Cumulative burn |
|---|---|---|---|
| 0 | 200,000 | 200,000 | 200,000 |
| 1 | 216,000 | 184,000 | 384,000 |
| 2 | 233,280 | 166,720 | 550,720 |
| 3 | 251,942 | 148,058 | 698,778 |
| 4 | 272,098 | 127,902 | 826,680 |
| 5 | 293,866 | 106,134 | 932,814 |
| 6 | 317,376 | 82,624 | 1,015,438 |
| 7 | 342,766 | 57,234 | 1,072,672 |
| 8 | 370,187 | 29,813 | 1,102,485 |
| 9 | 399,802 | 198 | 1,102,683 |

Revenue crosses expenses around month 9, and total cumulative burn to get there (~$1.1M) is well under the $2M cash on hand, leaving roughly $900k of buffer. **This company is default alive** — even with zero further fundraising, its current growth rate carries it to profitability before the cash runs out.

## Applying it for a client

Report gross burn, net burn, runway, and burn multiple together every month — presenting any one alone hides the story the other three tell. Run the default-alive projection with the client's own numbers whenever they're deciding *not* to raise ("we don't need the money right now") — it turns a gut feeling into a month-by-month table they can defend to their own board. Trigger a fundraising conversation the moment runway drops under ~9–12 months, not when it hits 3 — raises take 3–6 months end to end, and a founder negotiating from 2 months of runway will accept a much worse deal than one negotiating from 9. Use burn multiple to settle "are we growing efficiently" arguments concretely instead of vibes — a rising burn multiple quarter over quarter, even alongside rising ARR, is the earliest hard signal that growth is getting more expensive to buy.

## Watch-outs

- Gross and net burn get conflated constantly — always specify which one is being quoted; net burn is what actually determines runway.
- A single month's burn is noisy (annual contract payments, one-off hires, a big vendor invoice); use a trailing 3-month average for runway, not one month's snapshot.
- Burn multiple gets distorted by lumpy, front-loaded annual contract cash collections vs. the ARR they represent — reconcile against the smoother [revenue-recognition-saas-metrics.md](revenue-recognition-saas-metrics.md) figures before reacting to a spike.
- "Default alive" requires genuine, sustained growth *and* a real path where revenue overtakes flat expenses — a company that's default alive only because it assumes expenses never grow again is fooling itself; rebuild the projection with a realistic (non-zero) expense growth rate too.
- Runway and burn multiple can tell opposite stories (see the worked example above: efficient burn multiple, but thin runway) — always read both before concluding the company is "healthy."

## Related

- [unit-economics.md](../finance/unit-economics.md) — a bad burn multiple is almost always unit economics (LTV:CAC, payback) breaking down at the cohort level, not a burn problem in isolation.
- [13-week-cash-flow-forecast.md](../finance/13-week-cash-flow-forecast.md) — runway is the monthly, strategic view of cash; the 13-week forecast is the weekly, tactical view for when things are tight.
- [venture-debt-alternative-financing.md](../finance/venture-debt-alternative-financing.md) — a common tool for extending runway between equity rounds without diluting at a bad price.
- [cash-flow.md](../finance/cash-flow.md) — net burn is the same operating-cash-flow logic applied at a monthly operating cadence.
