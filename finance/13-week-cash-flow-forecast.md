---
domain: finance
concept: 13-Week Cash Flow Forecast (Rolling Liquidity Control)
source: research — standard turnaround/restructuring practice (Turnaround Management Association; CRO/advisory methodology)
tags: [cash-flow, liquidity, forecast, treasury, turnaround]
---

# 13-Week Cash Flow Forecast (Rolling Liquidity Control)

The 13-week cash flow forecast is a weekly — not monthly — rolling view of actual cash receipts and disbursements over the next quarter, built to catch a liquidity crunch with enough lead time to actually do something about it: payroll due before a big receivable clears, a loan payment landing the same week as a large supplier invoice. It's the standard tool lenders and turnaround/restructuring advisors require as a condition of a loan or forbearance in distressed situations, but the discipline is valuable for any business with lumpy cash timing, not only distressed ones.

## When to use

- Cash is tight or runway (see [burn-rate-runway.md](burn-rate-runway.md)) has dropped under roughly 6 months.
- A lender or creditor requires weekly liquidity visibility as a condition of financing, forbearance, or a covenant waiver.
- The business has lumpy receipts or payments — seasonal revenue, large contracts, payroll-heavy cost structure.
- As a standing weekly discipline throughout any turnaround, restructuring, or CRO engagement.

## How it works

**Structure — three blocks per week:**

| Block | Contains |
|---|---|
| Cash receipts | Customer collections, financing draws, asset sales — by source |
| Cash disbursements | Payroll, rent, COGS/suppliers, debt service, taxes, capex — by category |
| Net cash position | Opening balance + receipts − disbursements = closing balance (→ next week's opening) |

**Rolling mechanic.** As each week completes, its forecast is replaced with actuals, the oldest week drops off the front, and a new week is added 13 weeks out at the end — the view always stays 13 weeks forward and never shrinks toward zero.

**Variance tracking.** Every week, compare that week's actuals against what was forecast 1, 4, and 13 weeks earlier. A forecast that's consistently wrong in the same direction (collections always coming in below plan, say) is a signal to recalibrate the underlying assumption — not just to re-type next week's number.

**Minimum cash threshold.** Set a floor — commonly sized to cover a fixed number of weeks of non-negotiable obligations (payroll, rent, debt service) — below which the company must not fall. Any week where the *projected* closing balance dips under that floor triggers a mitigation review before that week arrives, not after: accelerate collections, delay non-critical payables, draw a credit line, or pause discretionary spend. Also build a downside scenario (e.g., collections 15% below forecast) to see how much lead time that shaves off the breach date.

## Example

A company opens week 1 with $400,000 cash and sets a minimum cash threshold of $150,000 (2 weeks of payroll and fixed obligations). Base weekly receipts run $195,000 and base weekly disbursements $205,000; payroll is biweekly, adding $60,000 in weeks 2, 4, 6, 8, 10, 12; a one-time $80,000 supplier catch-up payment is due in week 9; and a large customer contract payment of $220,000 is expected in week 11.

| Week | Opening | Receipts | Disbursements | Net | Closing |
|---|---|---|---|---|---|
| 1 | 400,000 | 195,000 | 205,000 | −10,000 | 390,000 |
| 2 (payroll) | 390,000 | 195,000 | 265,000 | −70,000 | 320,000 |
| 3 | 320,000 | 195,000 | 205,000 | −10,000 | 310,000 |
| 4 (payroll) | 310,000 | 195,000 | 265,000 | −70,000 | 240,000 |
| 5 | 240,000 | 195,000 | 205,000 | −10,000 | 230,000 |
| 6 (payroll) | 230,000 | 195,000 | 265,000 | −70,000 | 160,000 |
| 7 | 160,000 | 195,000 | 205,000 | −10,000 | **150,000** |
| 8 (payroll) | 150,000 | 195,000 | 265,000 | −70,000 | **80,000 ← breach** |
| 9 (catch-up) | 80,000 | 195,000 | 285,000 | −90,000 | **−10,000 ← negative** |
| 10 (payroll) | −10,000 | 195,000 | 265,000 | −70,000 | −80,000 |
| 11 (big receipt) | −80,000 | 415,000 | 205,000 | +210,000 | 130,000 |
| 12 (payroll) | 130,000 | 195,000 | 265,000 | −70,000 | 60,000 |
| 13 | 60,000 | 195,000 | 205,000 | −10,000 | 50,000 |

Built in week 1, this forecast already shows a threshold breach in week 8 and negative cash in week 9 — **7 weeks of lead time** before the actual problem hits, far more than a monthly cash review would surface (which might not flag week 8's issue until the month is nearly over).

**Mitigation, applied at week 1.** Two purely timing-based moves: delay the week 9 supplier catch-up payment to week 12, and pull forward $100,000 of the week 11 customer receivable into week 8 (partial early-payment arrangement). Re-running the forecast: week 8's closing rises from 80,000 to 180,000 (clears the threshold), and the low point shifts from week 9's −10,000 to week 10's 100,000 — softer, but week 10 still dips under the 150,000 threshold. **Both the original and the mitigated forecast end week 13 at the same $50,000** — resequencing moves *when* the crunch happens, it doesn't create new cash. If the 13-week total still ends thin or negative after resequencing everything that can be resequenced, the fix is new financing or real cost cuts, not further rearranging the calendar.

## Applying it for a client

Build the model in a simple spreadsheet, categorized by receipt/disbursement type, and refresh it every single week without fail — the discipline of the weekly refresh is what catches problems early, not the spreadsheet template itself. Set the minimum cash threshold explicitly with the client rather than leaving it implicit, so a projected breach triggers a scheduled response instead of being noticed only after it happens. Use variance-to-forecast as an ongoing credibility check on the client's own assumptions: if collections consistently miss forecast by a stable margin, haircut future receipts by that same margin rather than trusting the raw number next week too.

## Watch-outs

- The forecast is only as good as its inputs — treat unconfirmed receivables (verbal promises, not signed contracts/invoices) with a heavy discount or exclude them entirely.
- Skipping the weekly actual-vs-forecast reconciliation turns this into a one-time exercise instead of the rolling control it's meant to be.
- Don't let "the model says we're fine" replace judgment — one large expected receipt slipping a single week can flip the entire 13-week picture, so explicitly sensitize the forecast to that risk rather than treating the base case as settled.
- Resequencing (delaying payables, pulling forward receivables) only shifts *when* a cash crunch happens — it cannot fix a structural shortfall in the 13-week total; confirm which problem you're actually solving before declaring the crisis handled.
- This is a liquidity tool, not a profitability tool — a business can pass every week of a 13-week cash test while still being fundamentally unprofitable; cross-check against [burn-rate-runway.md](burn-rate-runway.md) and [break-even-and-roi.md](../finance/break-even-and-roi.md).

## Related

- [cash-flow.md](../finance/cash-flow.md) — the monthly, statement-level view of the same operating/investing/financing cash movement this forecast tracks weekly.
- [burn-rate-runway.md](../finance/burn-rate-runway.md) — runway is the strategic, monthly-cadence view; this is the tactical, weekly-cadence view for when things are tight.
- [break-even-and-roi.md](../finance/break-even-and-roi.md) — clearing every week of a 13-week cash test doesn't mean the underlying business has cleared break-even.
- [startup-financial-modeling.md](../finance/startup-financial-modeling.md) — the same driver-based discipline applied here at a weekly, near-term horizon instead of a quarterly/annual one.
