---
domain: finance
concept: Venture Debt & Alternative (Non-Dilutive) Financing
source: research — venture debt market practice (SVB, Hercules Capital, TriplePoint et al.)
tags: [debt, financing, non-dilutive, bridge, venture-debt]
---

# Venture Debt & Alternative (Non-Dilutive) Financing

Venture debt and its relatives (revenue-based financing, bridge notes, mezzanine debt) let a company raise capital alongside or between equity rounds without selling ownership at equity-round prices. It exists because lenders can underwrite off the credibility of a company's existing VC backers and its recent raise, not off traditional credit history — which is what makes debt available to pre-profit startups at all. Used well, it extends runway or funds a specific financeable need for a fraction of the dilution an equivalent equity round would cost; used to paper over broken unit economics, it just adds a senior creditor ahead of equity in a bad outcome.

## When to use

- Extending runway between equity rounds without triggering a down-round or accepting heavy dilution.
- Funding a specific, financeable asset — working capital, inventory, receivables — instead of using expensive equity capital for it.
- Bridging to a priced round that's highly likely but not yet closed.
- A capital-efficient, growth-stage company with predictable recurring revenue that can comfortably service fixed debt payments.

## How it works — the menu, roughly by cost/dilution

| Instrument | Dilution | Typical cost | Repayment | Best fit |
|---|---|---|---|---|
| **Venture debt (term loan)** | ~1–3% (via warrants) | Interest + warrant coverage + covenants | Fixed schedule, 2–4 yr term | Post-raise, VC-backed, extending runway |
| **Revenue-based financing (RBF)** | None | Fixed % of revenue, up to a repayment cap | Scales with revenue, no fixed maturity | Predictable, high-margin recurring revenue |
| **Bridge financing** | Converts to equity | Discount/cap on conversion | Converts at next priced round | Gap-fill to an anticipated round |
| **Mezzanine debt** | Warrants/conversion rights | Higher interest, subordinated | Fixed schedule, longer horizon | Later growth-stage/PE, buyouts, recaps |

**Venture debt (term loan).** Typically sized at **20–35% of the most recent equity round**, with a 2–4 year term: an interest-only period followed by amortization. Lenders lean heavily on the quality of the company's existing VC backers and the recency of the last raise as their underwriting signal. Comes with **warrant coverage**, usually **10–20% of the loan amount** — but because warrants are priced at the last round's share price and represent a small slice of the fully-diluted cap table, the actual equity dilution is typically only **1–3%**, far less than raising the same dollar amount as equity. Expect financial covenants (minimum cash, minimum runway) and a lien on assets/IP.

**Revenue-based financing (RBF).** Repay as a fixed percentage of monthly revenue until a total repayment cap is reached — typically **1.3x–3x** the amount advanced. No warrants, no board seat, no fixed maturity date. Payments scale down automatically if revenue dips, which makes it a better fit than a fixed-payment loan for businesses with some revenue volatility.

**Bridge financing.** A short-term note — often a convertible note or a SAFE with a discount/cap — designed to fund the gap between now and an anticipated priced round, and structured to convert into that round's equity rather than be repaid in cash.

**Mezzanine financing.** Subordinated debt, behind any senior venture debt, generally used at later growth-stage or PE-backed companies for growth capital, buyouts, or recapitalizations rather than early-stage runway extension. Carries a higher interest rate plus an equity kicker (warrants or conversion rights) to compensate lenders for being subordinated.

## Example

A Series A company raised $10M at a $10M pre-money in its last round and wants to extend runway 6 months without another equity round.

**Venture debt option.** Raise a $3,000,000 term loan (30% of the last round), 4-year term, 12 months interest-only at 10% annual interest, warrant coverage 15% of the loan amount ($450,000 notional), priced at the last round's share price.

```
Monthly interest-only payment (year 1) = 3,000,000 × 10% / 12 = $25,000/month
Actual equity dilution from the warrants ≈ 1.5–2% (small slice of fully-diluted shares)
```

Compare to raising the same $3M as equity at a (likely down-round-risk) $10M pre-money:

```
Equity dilution = 3,000,000 / (10,000,000 + 3,000,000) = 3M / 13M ≈ 23%
```

The entire case for venture debt here is that gap: **~1.5–2% dilution vs. ~23%** for the same dollars. Quantify this explicitly for the client rather than leaving it as an abstract "debt is cheaper" claim.

**Revenue-based financing option** (if the company has $200,000 MRR and high gross margin): advance $1,000,000, repay at 6% of monthly revenue until the 1.5x cap ($1,500,000) is repaid.

```
Initial monthly payment = 200,000 × 6% = $12,000/month
```

Payment rises as revenue grows; total repayment period depends entirely on the revenue growth trajectory, not a fixed calendar.

## Applying it for a client

Only recommend venture debt once the company has committed, credible equity backers and revenue predictable enough to service fixed payments — it's a runway-extension tool for a company on a good trajectory, not a rescue tool for one that isn't; taking on debt during a declining trajectory just adds a senior claim ahead of equity in a shutdown. Always run the explicit dilution comparison (debt's ~1–3% vs. the equivalent equity round's dilution) — founders routinely underweight how cheap debt is relative to what they assume, and the comparison is usually the deciding factor. Read the covenants (minimum cash, minimum MRR) carefully before signing — a covenant breach triggers acceleration precisely when the company can least afford it, turning a runway-extension tool into the reason the company runs out of cash faster.

## Watch-outs

- Venture debt is not free capital — interest, warrant coverage, covenants, and a lien on assets/IP are real costs, just a different kind than equity dilution.
- Using debt to mask a fundamentally broken unit-economics problem (see [unit-economics.md](unit-economics.md)) just delays the reckoning and adds a senior creditor to the cap table before it arrives.
- RBF economics change dramatically with revenue volatility — always model a downside revenue scenario, not just the base case, before committing to the repayment cap.
- Mezzanine and mid-market venture debt terms vary widely by lender — compare at least two or three term sheets rather than accepting the first one offered.
- A lien on IP/assets from a venture debt lender can complicate or slow down a future acquisition or subsequent financing round — check what the lender's consent rights look like before signing, not after a buyer shows up.

## Related

- [burn-rate-runway.md](../finance/burn-rate-runway.md) — venture debt's main purpose is extending runway between rounds; size it against the actual runway gap, not a round number.
- [cap-tables-dilution.md](../finance/cap-tables-dilution.md) — the ~1–3% dilution from warrant coverage still needs to be modeled onto the fully-diluted cap table, not ignored because it's "small."
- [unit-economics.md](../finance/unit-economics.md) — debt taken on to cover a broken LTV:CAC ratio just delays the underlying problem; fix the unit economics first.
