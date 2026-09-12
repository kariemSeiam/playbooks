---
domain: finance
concept: Cap Tables & Dilution Mechanics
source: research — Y Combinator (Post-Money SAFE, 2018); Carta
tags: [cap-table, dilution, safe, equity, fundraising, options]
---

# Cap Tables & Dilution Mechanics

A cap table is the ownership ledger of a company — who owns what percentage, across founders, employees, and every investor, at every point in the company's life. Dilution is the mechanical reduction in existing holders' ownership *percentage* (not value) whenever new shares are issued — a SAFE converting, an option pool expanding, a new round pricing. Every fundraising conversation is ultimately a cap table conversation, and getting the mechanics wrong — especially around SAFEs and option pools — is one of the most common ways founders give away more of the company than they realize.

## When to use

- Before signing any term sheet — model the fully-diluted cap table forward through the round, not just the headline valuation.
- Whenever a client wants to know "what will I own after this raise" — the honest answer requires the pool size, SAFE conversion mechanics, and pro-rata terms, not just pre-money and investment amount.
- When creating or expanding an option pool — this is founder dilution disguised as "standard practice," and the size and timing are negotiable.
- When multiple SAFEs are stacked ahead of a priced round — sequencing and cap/discount terms materially change who ends up owning what.

## How it works

### Pre-money vs. post-money mechanics

```
Post-money valuation = Pre-money valuation + New investment
New investor ownership % = New investment / Post-money valuation
Existing holders' ownership % after = Existing % before × (Pre-money / Post-money)
```

### SAFE mechanics: pre-money (2013) vs. post-money (YC, 2018)

The original (pre-money) SAFE had a structural flaw: when multiple SAFEs stacked before a priced round, founders couldn't know their final ownership until *all* the SAFEs converted together with the new round — the more SAFE money raised, the more everyone's SAFE-implied ownership shifted unpredictably.

Y Combinator's **post-money SAFE** (2018) fixes this: each SAFE's ownership percentage is fixed and knowable the moment it's signed —

```
SAFE ownership % = Investment / Post-money valuation cap
```

— and that percentage does **not** change based on how much other SAFE money is raised alongside it. It is, however, still diluted by whatever happens *after* the SAFE round: the priced round's new investors and — critically — any option pool created or expanded as part of that priced round.

### Option pool and the "option pool shuffle"

An option pool is unallocated equity reserved for future employee hires — typically **10–20%** of the fully-diluted cap table post-raise. New investors in a priced round routinely require the pool to be created or topped up *before* the round closes, sized into the **pre-money** valuation. That means the pool's dilution is absorbed by existing holders (founders and prior SAFE/note holders) — not by the new investors writing the check. This is the "option pool shuffle," and it's the single most common source of founders being surprised by how little they end up owning after a round they thought they understood.

### Pro-rata rights

A contractual right, usually granted to earlier investors, to invest enough in a future round to maintain their current ownership percentage before new investors get access to that round's allocation. This reduces the room available for new investors in every subsequent round and should be tracked explicitly on the cap table, not left as a footnote in an old term sheet.

## Example

Founders start with 8,000,000 shares (100% of the company).

**Pre-seed:** raise $500,000 via a post-money SAFE at a $5,000,000 post-money cap.

```
SAFE ownership % = 500,000 / 5,000,000 = 10%
```

This 10% is fixed and doesn't move regardless of any other SAFE money raised alongside it — but it hasn't converted to shares yet, so today's actual share ledger is still 100% founder-owned; the 10% is a future claim.

**Series A:** pre-money $12,000,000, new investment $4,000,000 → post-money $16,000,000. New investor ownership = $4M / $16M = **25%**. The term sheet requires a **15%** post-round option pool, carved out of the pre-money — meaning founders (and the SAFE holder) bear that dilution, not the new investors.

The SAFE converts into this round (assume its $5M cap gives a better price than the round's own terms, so it converts at the cap). Before the option pool and new money are layered in, the pre-Series-A cap table is:

```
SAFE holder: 10%
Founders:    90%
```

The option pool (15%) and new Series A investors (25%) together take 40% of the fully-diluted post-round table. The remaining 60% splits between founders and the SAFE holder in their existing 90:10 ratio:

```
Founders post-Series A   = 60% × 90% = 54%
SAFE holder post-Series A = 60% × 10% = 6%
New Series A investors    = 25%
Option pool                = 15%
Total = 54 + 6 + 25 + 15 = 100%  ✓
```

Founders went from 100% to 54% across two rounds — with the 15-point option pool alone accounting for nearly as much dilution as the Series A investment itself. That's the number to show a founder *before* they sign, not after.

## Applying it for a client

Build the fully-diluted cap table before any term sheet is signed, and model it forward through at least the next two rounds so the founder sees where they actually land, not just the immediate post-money number. Negotiate the option pool's size and timing explicitly — "standard" doesn't mean "non-negotiable," and a smaller pool (topped up later, diluting future investors too) can materially change founder ownership. Track every pro-rata right on the cap table itself, not in a side letter nobody revisits, since it constrains how much allocation is available to new investors in every future round. Maintain the actual cap table in dedicated tooling (Carta is the standard) rather than a spreadsheet — a spreadsheet cap table goes stale the moment a SAFE converts or an option is exercised, and a client making decisions off a stale table is making them off wrong numbers. For a pre-seed client, hold total dilution to the **10–15%** target range per round and flag it clearly the moment stacked SAFEs push cumulative (undiluted-basis) dilution past that band.

## Watch-outs

- Ownership percentage and dollar value are not the same thing — a smaller stake in a much larger post-money can still be a bigger outcome; don't let "my % went down" alone drive a decision.
- Pre-money and post-money SAFEs are not interchangeable on the same cap table — mixing them without carefully modeling each one's conversion mechanics produces wrong numbers, not approximately-right ones.
- Option pool timing (created pre-round vs. post-round, sized into pre-money vs. post-money) changes who bears the dilution — always confirm which convention a term sheet is using.
- Multiple SAFEs at different caps and discounts converting simultaneously require careful sequencing (typically lowest cap/most favorable terms convert first) — never just sum their nominal percentages.
- Founders routinely lose track of cumulative dilution across several small pre-seed instruments; recompute the fully-diluted picture every time a new instrument is added, not just at the next priced round.

## Related

- [valuation-methods.md](../finance/valuation-methods.md) — pre-money and post-money valuations here are computed using the VC Method, Berkus, or Scorecard outputs from that note.
- [venture-debt-alternative-financing.md](../finance/venture-debt-alternative-financing.md) — non-dilutive debt is the main lever for extending runway without moving any of these percentages at all.
- [unit-economics.md](../finance/unit-economics.md) — the metrics an investor checks before agreeing to the valuation that drives this cap table math.
