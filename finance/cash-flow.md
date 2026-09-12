---
domain: finance
concept: Cash Flow
source: sources/finance/civiconnectors-financial-planning-management.pdf.card.md
tags: [cash-flow, liquidity, operating-activities, investing-activities, financing-activities]
---

# Cash Flow

The cash flow statement tracks every pound of cash actually entering and leaving a business over a period — separate from and often very different from the profit shown on the income statement. It matters because a company can be profitable on paper and still run out of cash to pay its bills; cash flow is what tells you whether that's about to happen.

## When to use

- A client is profitable but keeps feeling "broke" — cash flow, not the P&L, usually explains why (timing of receivables/payables, debt repayments, capital purchases).
- Before any funding ask — lenders and investors read the cash flow statement to judge whether the business can actually service debt or sustain itself, not just whether it reports a profit.
- To decide whether the business can afford a new hire, a piece of equipment, or a dividend/owner draw right now, versus on paper.
- Any time you need to assess liquidity — how fast assets convert to cash, and how fast cash is needed to cover liabilities.

## How it works

**Objectives of the cash flow statement:**
- Report cash receipts and payments within a limited period.
- Present that information split across operating, investing, and financing activities.
- Let investors judge whether the business can generate positive cash flow going forward, meet its obligations, distribute profits, and how much external financing it's likely to need.
- Assess liquidity — the time it takes to convert assets into cash versus the time available to pay liabilities.
- Let creditors gauge "financial ease" — the entity's ability to repay debts and meet payments when due.

**Why it's important (in practice):** short-term planning, a detailed statement of where the business actually spends, revealing surplus cash generated, informing long-term planning, verifying the business holds an optimal cash balance (not too little, not too much sitting idle), and general capital analysis.

**The three types of cash flow:**

| Type | What it captures |
|---|---|
| **Operating activities** | Cash in/out from normal, ongoing business — selling products, providing services, paying interest and taxes |
| **Investing activities** | Cash paid or received to acquire or dispose of long-term (fixed) assets |
| **Financing activities** | Everything not operating or investing — cash from issuing new shares/raising capital, cash from issuing long-term bonds, dividends paid to shareholders, cash paid to repay loans/bank facilities |

**Steps to prepare a cash flow statement:**

1. **Determine the starting balance** — pull this from the income statement for the reporting period.
2. **Calculate cash flow from operating activities** — reveals how much cash the company actually collected from running the business.
3. **Calculate cash flow from investing activities** — only include investing activity involving *free cash*, not debt-funded investing.
4. **Calculate cash flow from financing activities** — including dividends paid.
5. **Determine the final cash balance** — the change in net cash for the period equals the sum of the three activity flows; this is the total cash the company gained or lost over the reporting period.

```
Net cash flow = CFO + CFI + CFF
(where CFO/CFI/CFF are each net of that category's inflows minus outflows,
 and each can itself be positive or negative)
```

**Positive vs. negative cash flow:**
- **Positive** — the business's liquid assets are increasing. This is the state to maintain: it enables settling debts, reinvesting in the business, returning money to shareholders, paying expenses, and funding the future.
- **Negative** — a persistent negative *operating* cash flow specifically is the red flag: it means the business needs more external funds just to keep operating, and left unaddressed leads toward bankruptcy. (A single negative period from a large, deliberate investment purchase is not automatically alarming — check *which* category is negative before reacting.)

## Example

The source deck's own worked example (simplified, illustrative): a business estimates its costs across the three activities for a period — operating activities 100,000 EGP, financing activities 75,000 EGP, investing activities 50,000 EGP — and states net cash flow as the sum: 100,000 + 75,000 + 50,000 = 225,000 EGP.

Treat that literally-summed example with caution: it works only because all three figures were framed as net *inflows* for that period. In practice, each category's cash flow can run negative (e.g., financing activities are negative in a period where the business repays more debt than it raises), and you must net inflows against outflows within each category before summing across the three:

```
Net cash flow = (Operating in − Operating out)
              + (Investing in − Investing out)
              + (Financing in − Financing out)
```

A more realistic small-business version: a workshop pays 29,000 EGP/month in wages, 6,000 EGP rent, 1,500 EGP electricity, and buys 120,000 EGP of raw materials in the period (all operating outflows); separately it sells an old machine and buys a replacement (investing activity — net investing cash flow is the sale proceeds minus the purchase price); and it repays half of an 80,000 EGP debt, i.e. 40,000 EGP (a financing outflow). Each category nets to its own signed figure before the three are added — you cannot just add the raw cost numbers together, or debt repayment and materials cost would wrongly look like the same kind of "expense."

## Applying it for a client

Build the cash flow statement monthly, not annually, for any client with tight working capital — a monthly view is what actually catches a liquidity crunch before it happens (payroll due before a big invoice clears, a supplier payment landing the same week as a loan repayment). Split the three categories every time, even for a tiny business: it's the fastest way to show a client *why* they're cash-poor despite being profitable — usually it's financing (debt repayment) or investing (equipment purchase) eating cash that operations generated, not the operations themselves failing. If operating cash flow is negative more than one period running, treat that as the priority fire to put out over any growth initiative — a business can survive a bad investing or financing quarter; it cannot survive sustained negative operating cash flow.

## Watch-outs

- Cash flow is not profit. A business can show a healthy net profit on the income statement and still have negative cash flow (e.g., large uncollected receivables, big inventory build-up, upfront capital purchases) — always check both, never one as a proxy for the other.
- Don't include debt-funded investing activity in the investing section — the deck is explicit that only *free cash* investing activity belongs there; debt-funded purchases flow through financing.
- A single negative period isn't automatically bad (e.g. a deliberate equipment purchase); a *persistent* negative operating cash flow is the real warning sign — diagnose which of the three categories is driving it before reacting.
- Watch for clients (and slide decks) that casually sum raw cost figures across categories without netting inflows against outflows first — that produces a number that looks like "net cash flow" but isn't.

## Related

- [budgeting.md](../finance/budgeting.md) — a budget forecasts profit and expense; cash flow tracks when money actually moves, and the two routinely diverge.
- [break-even-and-roi.md](../finance/break-even-and-roi.md) — clearing break-even or showing a strong ROI doesn't guarantee the cash arrives in time to keep the business solvent.
- [income-statement-vs-balance-sheet.md](../finance/income-statement-vs-balance-sheet.md) — the starting balance in step 1 is pulled directly from the income statement.
