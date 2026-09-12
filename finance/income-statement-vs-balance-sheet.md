---
domain: finance
concept: Income Statement (P&L) vs. Balance Sheet
source: sources/finance/civiconnectors-financial-planning-management.pdf.card.md
tags: [income-statement, profit-and-loss, balance-sheet, financial-statements]
---

# Income Statement (P&L) vs. Balance Sheet

The income statement (profit & loss statement) reports whether a business made or lost money *over a period*; the balance sheet reports what a business owns and owes *at a single point in time*. Confusing the two — or worse, presenting one when a client actually needs the other — is one of the most common ways a financial conversation with a client goes wrong.

## When to use

- **Income statement:** whenever the question is "did we make money, and where did it come from/go?" — pricing decisions, cost-control conversations, loan applications, quarterly performance reviews.
- **Balance sheet:** whenever the question is "what is this business actually worth right now, and what does it owe?" — valuation conversations, solvency checks, before taking on debt or investment.
- Use both together whenever you're assessing overall financial health — profitability (income statement) without a check on solvency (balance sheet) is an incomplete picture, and vice versa.

## How it works

**Income statement (P&L) — what it is:** a financial statement reporting a company's financial performance over a specific accounting period (usually a fiscal quarter or longer). It summarizes revenues, costs, and expenses incurred over that period, showing whether the company can generate profit and pointing at the two levers to fix if it can't: increase revenue, or reduce cost (or both).

**Income statement objectives:**
- Determine the facility's performance and help investors evaluate it.
- Determine profitability and explain the revenues/expenses behind it.
- Give managers the basis for future decisions, planning, and strategy.
- Support share-price appreciation on the stock exchange when profits rise.
- Show the entity's financial ability to meet its obligations.
- Support bank/financial-institution decisions on loans and similar matters.

**Income statement line items:**

| Category | Contains |
|---|---|
| Revenues | All revenue earned from selling products or services |
| Expenses | Cost of goods sold: production cost of goods, operating expenses, depreciation, interest expense, tax expense |
| Profits (non-operating) | Amounts not tied to core operations — e.g. gains from selling assets, gains from selling investments, plus total/operating profit |
| Losses (non-operating) | Any losses incurred that are unrelated to core operations |

**Two ways to build it:**

1. **One-step (single-step) income statement** — all revenue (operating + non-operating) in one line, offset by all expenses (operating + non-operating) in one line; subtract total expenses from total revenue to get net profit/loss directly. Fast to build, but it never isolates *operating* profit, so it's weak for judging how well the core business itself performs.

2. **Multi-step income statement** — separates operating revenue/expense from non-operating revenue/expense, so you arrive at an operating profit figure before non-operating items adjust it down to net income. Slower to build (more line items), but it's the version that actually tells you whether the core business is healthy, independent of one-off gains or losses.

**Balance sheet:** reports assets, liabilities, and shareholders' equity as of a specific date — a snapshot, not a flow. It's built from the same identity used in a budget template (see [budgeting.md](budgeting.md)): Assets = Liabilities + Equity.

**The actual differences, precisely:**
- **Period vs. point in time** — the income statement covers a *span* (a quarter, a year); the balance sheet is a *snapshot* taken on one date. This is the fundamental distinction: everything else follows from it.
- **What each tells you** — the income statement shows how healthy and profitable the business *was over that stretch*; the balance sheet shows what the business owns and owes, plus long-term investments, *right now*.
- **The bottom-line number** — the income statement's headline number is net income (a flow); the balance sheet's is the company's actual net worth at that moment (a stock).

## Example

**One-step income statement** (Establishment A, 2019): sales revenue 100,000 EGP, investment income 75,000 EGP. Expenses: operating 40,000, marketing 15,000, admin & general 10,000, other 5,000.

```
Total revenue  = 100,000 + 75,000 = 175,000 EGP
Total expenses = 40,000 + 15,000 + 10,000 + 5,000 = 70,000 EGP
Net income     = 175,000 − 70,000 = 105,000 EGP
```

Notice this tells you the business made 105,000 EGP net — but not how much of that came from actually operating the business versus investment income. That's the one-step method's blind spot.

**Multi-step income statement** (Establishment B, 2020): sales revenue 100,000 EGP, cost of goods sold 20,000 EGP, total operating expenses 20,000 EGP.

```
Gross profit     = 100,000 − 20,000 = 80,000 EGP
Operating profit = 80,000 − 20,000 = 60,000 EGP        ← core-business performance, isolated
```

Then the non-operating items for the period: loss on sale of a building (5,000), an equipment-related expense (4,000), a gain on sale of land in May 2020 (20,000), interest expense on a bank loan (10,000), tax expense (7,000):

```
Net income = 60,000 − 5,000 − 4,000 + 20,000 − 10,000 − 7,000 = 54,000 EGP
```

The multi-step version shows both numbers — a healthy 60,000 EGP operating profit, and a lower 54,000 EGP net income after one-off items and financing costs. A one-step statement would have shown only the 54,000 EGP, hiding the fact that the core business is actually performing better than the bottom line suggests.

## Applying it for a client

Default to the multi-step income statement for any client past the very first weeks of trading — the operating-profit line is what tells you whether the *business itself* works, independent of a one-off asset sale or a bad debt write-off skewing the final number. When a client says "we made X profit this year," always ask whether that's operating profit or net income including one-off items — the gap between the two is where a lot of false confidence (or false alarm) lives. Pair the income statement with a balance sheet before any lending or investment conversation: a client can show a great income statement while quietly becoming insolvent (mounting liabilities, shrinking equity), and the P&L alone will never surface that — only the balance sheet will.

## Watch-outs

- Never present a single-step income statement as if it shows operating health — it structurally cannot, because it never isolates operating profit from non-operating items.
- "Profit" language gets thrown around loosely by clients — always pin down whether they mean gross profit, operating profit, or net income; these differ by exactly the line items shown in the multi-step example above.
- A profitable income statement is not evidence of solvency — check the balance sheet before concluding the business is financially sound.
- The balance sheet's numbers are only true as of its date — a client's balance sheet from six months ago can be stale even if the income statement trend looks fine.

## Related

- [cash-flow.md](../finance/cash-flow.md) — the cash flow statement's starting balance is pulled from the income statement, but cash flow and net income routinely diverge.
- [budgeting.md](../finance/budgeting.md) — the balance-sheet-style assets = liabilities + equity structure is the same template used to lay out a budget.
- [break-even-and-roi.md](../finance/break-even-and-roi.md) — "financial performance" pulls together the income statement, balance sheet, cash flow statement, and equity statement into one comparative view.
