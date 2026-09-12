---
domain: finance
concept: Budgeting
source: sources/finance/civiconnectors-financial-planning-management.pdf.card.md
tags: [budget, budget-preparation, financial-planning, early-stage]
---

# Budgeting

A budget is a structured forecast of a company's revenues and expenses over a fixed future period (typically the next fiscal year) that turns financial goals into a spending and earning plan. It matters because it forces a business to decide in advance what it will spend money on, surface wasted expenses before they happen, and give management a yardstick to check actual performance against.

## When to use

- A client is about to enter a new fiscal year and has no formal spending plan, or is still running on "whatever's in the account."
- Revenue or costs have shifted materially (new product, new hire, price change) and last year's numbers no longer reflect reality.
- You need a baseline to catch overspend early, not after the bank balance already shows it.
- Before requesting external financing — lenders and investors expect to see a budget, not a bank statement.

## How it works

**Definition in practice:** a budget is a summary of expected revenues and expenses for a specific period, used to manage money, set spending priorities, and identify/reduce wasted expense.

**Budget preparation — the process, in order:**

1. **Update budget assumptions** — review every assumption about the company's operating environment that the budget rests on (cost of materials, headcount, demand), and revise any that are stale.
2. **Determine available financing** — pin down how much money will actually be available to fund operations during the budget period. A budget built on financing that won't materialize is fiction.
3. **Identify cost points** — determine the nature of costs tied to the period's planned activities: their financial value, and the type/level of activity that generates them (this is where you separate fixed from variable costs — see [break-even-and-roi.md](break-even-and-roi.md) for that split).
4. **Create the draft budget** — pull the prior year's base budget, update it with the current year's actual expenses, and layer in the expected nature of next year's funding.
5. **Obtain revenue forecasts** — get the expected revenue percentage/growth from the sales function, have the CEO (or owner) sanity-check its realism, then push it down to department heads as the basis for their own department budgets.
6. **Collect departmental budgets** — gather every department's financial submissions, check them for errors, and reconcile against other known financial data.
7. **Review the financial budget** — the management team meets to walk every line item, flag expected restrictions (including financing-driven ones), then send the budget back to whoever built it (accounting/finance team) for correction.
8. **Upload the budget** — load the finalized numbers into the financial system so actuals can be tracked against budget going forward.

**Budget components / template structure** — a budget is laid out like a balance sheet, split into two mirrored sides:

| Assets side | Liabilities & equity side |
|---|---|
| Trading assets → Total trading assets | Short-term liabilities → Total liabilities |
| Fixed assets → Total fixed assets | Property (equity) → Total property |
| **Total assets** | **Total liabilities & property** |

Both sides must reconcile (Total assets = Total liabilities & property), the same identity that governs a balance sheet.

## Example

A small bakery preparing its Year 2 budget:

- **Step 1 (assumptions):** flour and butter prices rose ~12% this year; update the cost assumption.
- **Step 2 (financing):** owner has EGP 150,000 in retained cash plus a EGP 50,000 overdraft facility available — EGP 200,000 total to fund the year.
- **Step 3 (cost points):** rent (fixed, EGP 6,000/month) vs. ingredients (variable, scales with units baked).
- **Step 4 (draft):** last year's budget was EGP 900,000 revenue / EGP 750,000 expenses; update with this year's actual EGP 980,000 revenue / EGP 810,000 expenses as the new base.
- **Step 5 (revenue forecast):** sales lead projects 15% growth next year off the new base → EGP 1,127,000.
- **Step 6–7 (departmental review + sign-off):** kitchen, front-of-house, and delivery each submit their cost lines; owner and accountant review together and flag that the delivery line assumes financing that isn't secured yet.
- **Step 8 (upload):** final numbers go into the bookkeeping software so monthly actuals can be tracked against this plan.

## Applying it for a client

Most early-stage clients don't have a "budget" — they have a bank balance and a vibe. Don't hand them a finance-department process; compress it to three things they can actually run: (1) last year's real numbers (or, if pre-revenue, a bottom-up cost estimate) as the starting point, (2) a one-line-per-cost-category fixed-vs-variable split (this doubles as break-even inputs — do it once, use it twice), (3) a revenue forecast they can defend out loud, sanity-checked against pipeline or comparable-business benchmarks, not wishful thinking. Skip steps 6–8 (departmental review, system upload) entirely for a single-owner business — those exist for companies with departments. Revisit the budget monthly against actuals; a budget nobody checks is worthless within a quarter.

## 2024→2026: Modern FP&A

The eight-step process above describes the classical annual-budget cycle — and by 2026 a lot of that cycle is treated as a liability, not a discipline, at any company that can move faster than once a year.

**Rolling forecasts replace the static annual budget.** Instead of locking a 12-month plan every December and defending it against reality for the rest of the year, mature FP&A teams now run a continuously rolling 12–18 month forecast, refreshed monthly or quarterly — so the plan is always looking 12+ months forward and updates as real data comes in, rather than waiting for the next annual cycle. Status: battle-tested; this is now the default recommendation for any growth-stage company, not a fringe practice.

**Driver-based models replace percentage-based line-item budgets.** "Grow marketing spend 10%" gives way to explicit driver assumptions (leads/month, conversion rate, sales headcount, cost per hire) that tie directly into a linked 3-statement model (see [startup-financial-modeling.md](startup-financial-modeling.md)) — so a single driver change, like a hiring plan slipping a quarter, automatically recalculates every downstream number instead of requiring a manual re-forecast of every line.

**Zero-based budgeting (ZBB)** requires every line item to be justified from zero each cycle, rather than carried forward as "last year plus inflation" — directly replacing step 4's "pull the prior year's base budget" instinct. McKinsey's research across ZBB implementations reports 10–25% aggregate cost reductions, landing in the P&L within 4–6 months, with 50–75% reductions achievable in specific targeted cost categories when a company commits to a genuinely aggressive, zero-based review rather than a token exercise. Status: battle-tested.

**"Beyond Budgeting"** (the movement associated with the Beyond Budgeting Round Table) goes further: it argues the fixed annual budget itself — a target set 12 months in advance and then used to judge performance — creates the wrong incentives (sandbagging targets, spending down remaining budget in Q4 to avoid a cut next year). It replaces the fixed budget with adaptive, relative targets (benchmarked against peers or prior periods) and decentralizes forecasting ownership to the operating teams closest to the numbers, rather than centralizing it in the departmental-review steps (6–7) above. Status: battle-tested as a philosophy, though full adoption remains rarer than rolling forecasts or ZBB individually.

**AI-assisted FP&A** is the newest layer: platforms like Jirav, Anaplan, and Drivetrain now auto-generate baseline forecasts from historical driver data, flag anomalous spend or variance in near-real-time instead of at month-end close, and let a planner run scenario models (base/bull/bear — see [startup-financial-modeling.md](startup-financial-modeling.md)) directly inside the planning tool instead of in a disconnected spreadsheet. This sits on top of **connected planning** — one shared model where sales, headcount, and finance assumptions live together, so a change in one team's plan flows through automatically instead of requiring the manual departmental reconciliation steps 6–7 describe. Status: emerging-but-credible — the tooling is real and adopted at scale, but treat vendor-claimed accuracy gains with the same skepticism applied to any forecasting tool, and always sanity-check an AI-generated baseline against driver assumptions a human on the team can defend.

## Watch-outs

- A budget built purely by inflating last year's actuals bakes in last year's inefficiencies — always re-question assumptions (step 1), don't just index them up.
- Revenue forecasts that skip the "CEO/owner realism check" step are the single most common source of a budget that's dead on arrival.
- Confusing "budget" with "cash flow" — a budget is a planned P&L for a period; it does not tell you when cash actually lands or leaves (see [cash-flow.md](cash-flow.md) for that).
- For a very small business, formal multi-department review steps are overhead, not rigor — cut them, don't skip the underlying discipline (assumptions, financing reality, revenue defensibility).

## Related

- [cash-flow.md](../finance/cash-flow.md) — a budget plans profit and expense; cash flow tracks the timing of actual money movement.
- [break-even-and-roi.md](../finance/break-even-and-roi.md) — the fixed/variable cost split done in step 3 is the same split break-even analysis needs.
- [financial-planning-process.md](../finance/financial-planning-process.md) — budgeting is the short/annual-cycle output; financial planning is the longer-horizon frame it sits inside.
- [income-statement-vs-balance-sheet.md](../finance/income-statement-vs-balance-sheet.md) — the budget template mirrors the balance sheet's assets = liabilities + equity structure.
- [startup-financial-modeling.md](../finance/startup-financial-modeling.md) — the driver-based, rolling-forecast approach in "2024→2026" above is the same 3-statement modeling discipline covered in full there.
