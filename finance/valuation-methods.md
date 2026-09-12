---
domain: finance
concept: Startup Valuation Methods (Stage-Appropriate Triangulation)
source: research — Aswath Damodaran (NYU Stern); Berkus Method (Dave Berkus); Scorecard Method (Bill Payne); VC Method (Bill Sahlman, HBS, 1987)
tags: [valuation, dcf, comparables, vc-method, fundraising]
---

# Startup Valuation Methods (Stage-Appropriate Triangulation)

Valuing a startup is fundamentally different from valuing a mature company because the inputs that make standard methods work — revenue, cash flow, comparable public companies — often don't exist yet. The right response isn't to force a DCF onto a pre-revenue company; it's to triangulate 2–3 stage-appropriate methods and reconcile the gap between them out loud. Aswath Damodaran (NYU Stern) is the standard academic reference for valuation generally; the Berkus Method, the Scorecard Method, and the VC Method are the practitioner tools that fill the gap DCF and comparables leave at the earliest stages.

## When to use

- **Pre-revenue / pre-seed:** Berkus Method and/or Scorecard Method — there's no revenue or cash flow to discount, so value the qualitative risk factors instead.
- **Seed / Series A (early revenue):** VC Method, cross-checked against comparable recent deals/multiples in the sector.
- **Series B and later (established revenue, clearer trajectory):** DCF, precedent transactions, and public/private comparables.
- Any negotiation where a client or investor is anchoring on a single number — triangulating a second method is the fastest way to test whether that number is defensible.

## How it works

### Berkus Method (pre-revenue)

Created by Dave Berkus in the 1990s, it assigns up to **$500,000** to each of five qualitative risk factors, for a maximum pre-money valuation of **$2.5M** for a company with zero revenue:

| Dimension | Risk it addresses | Max value |
|---|---|---|
| Sound idea | Product/basic value risk | $500,000 |
| Prototype | Technology risk | $500,000 |
| Quality management team | Execution risk | $500,000 |
| Strategic relationships | Market risk | $500,000 |
| Product rollout or early sales | Production/financial risk | $500,000 |

Score each dimension on the evidence in hand (not aspiration), sum the five, and that's the pre-money valuation.

### Scorecard Method (Bill Payne, seed stage)

Start from the average pre-money valuation of recently-funded, comparable companies in the same region and sector, then adjust it with weighted comparison factors:

| Factor | Weight |
|---|---|
| Management team | 0–30% |
| Size of the opportunity | 0–25% |
| Product/technology | 0–15% |
| Competitive environment | 0–10% |
| Marketing/sales channels & partnerships | 0–10% |
| Need for additional financing | 0–5% |
| Other | 0–5% |

For each factor, score the target company relative to "average" (100%) — stronger scores above 100%, weaker below — multiply each factor's score by its weight, sum the weighted scores into an overall multiplier, and apply that multiplier to the regional average pre-money.

### VC Method (Bill Sahlman, HBS, 1987)

Built for pre-revenue-to-early-revenue companies where an investor is thinking backward from a target exit:

```text
Terminal (exit) value = Projected exit-year revenue × industry exit multiple
                          (or exit-year net income × exit P/E)
Post-money valuation   = Terminal value / Required ROI
Pre-money valuation    = Post-money valuation − Investment amount
Ownership %            = Investment / Post-money valuation
```

Required ROI for early-stage risk typically runs **10x–30x over a 5–8 year hold** — much higher than public-market discount rates, because it has to compensate for the high failure rate across an entire portfolio, not just this one company.

**The step most people skip — future dilution adjustment.** The ownership % above is what the investor needs to hold *at exit*. But future rounds will dilute everyone, including this investor. If the company is expected to raise, say, two more rounds each diluting existing holders by ~20%:

```text
Required ownership TODAY = Required ownership at exit / [(1 − d₁) × (1 − d₂) × ...]
```

Skipping this step is the single most common way a VC-method valuation understates what an investor should actually negotiate for — and, from the founder's side, is the reason the ownership ask in a term sheet is routinely higher than the naive math above suggests.

### DCF (Series B+ / established revenue)

```text
EV = Σ [FCFₜ / (1+r)ᵗ]  for t = 1..n   +   TV / (1+r)ⁿ
TV (Gordon growth) = FCFₙ × (1+g) / (r − g)
```

Use a venture-adjusted discount rate (often 25–40%+, not a public-market WACC) to reflect early-stage risk, since standard WACC understates it. DCF only becomes reliable once a company has a demonstrated, reasonably stable growth trajectory — this is Damodaran's own caution, not just a modeling nicety.

### Precedent transactions & comparables (Series B+)

The mechanic is a simple multiple applied to the target's own metric:

```text
Implied valuation = Comparable multiple × Target's metric
```

- **Comparables** — take a revenue or EBITDA multiple observed across a set of similar public or recently-financed private companies (same sector, similar growth rate and margin profile), and apply it to the target's own revenue or EBITDA.
- **Precedent transactions** — the same idea, but the multiple is drawn from actual completed M&A deals for comparable companies rather than current trading/financing multiples; precedent-transaction multiples typically run higher than public comparables because they include a control premium.

The entire method lives or dies on how truly comparable the reference set is — stage, growth rate, margin structure, and geography all need to line up, or the multiple looks precise while being irrelevant. Use comparables as a cross-check against the VC method or DCF output, not as a standalone number.

## Example

**Berkus, worked.** A pre-revenue startup: sound idea scores $400,000 of $500,000 (strong but unproven thesis); working prototype scores $350,000; founding team with two prior exits scores the full $500,000; signed LOIs with two strategic distribution partners score $300,000; no revenue yet scores $0 of $500,000.

```text
Pre-money = 400,000 + 350,000 + 500,000 + 300,000 + 0 = $1,550,000
```

**VC Method, worked (with the future-dilution step most models skip).** An investor puts in $2,000,000. They project the company exits in 6 years at $80M revenue, with an industry-standard 4x revenue exit multiple, and they require a 15x return over that hold.

```text
Terminal value = 80,000,000 × 4 = $320,000,000
Post-money (naive) = 320,000,000 / 15 = $21,333,333
Pre-money (naive)  = 21,333,333 − 2,000,000 = $19,333,333
Ownership at exit (naive) = 2,000,000 / 21,333,333 = 9.4%
```

Now adjust for two expected future rounds, each diluting existing holders ~20%:

```text
Required ownership TODAY = 9.4% / (0.8 × 0.8) = 9.4% / 0.64 = 14.7%
Implied post-money for $2M at 14.7% ownership = 2,000,000 / 0.147 = $13,600,000
Implied pre-money = 13,600,000 − 2,000,000 = $11,600,000
```

The dilution-adjusted pre-money ($11.6M) is materially lower than the naive number ($19.3M) — this is the gap that actually gets negotiated in the room, and it's the single biggest reason a founder and an investor can each do the "same" VC-method math and land on very different valuations.

**DCF, worked (illustrative Series B).** Projected free cash flow: $2M, $3M, $5M, $7M, $10M over years 1–5, terminal growth 3%, discount rate 30%.

```text
TV at year 5 = 10 × 1.03 / (0.30 − 0.03) = 10.3 / 0.27 = $38.15M
Discounted TV = 38.15 / (1.30)^5 = 38.15 / 3.71 = $10.28M
Discounted FCFs: 1.54 + 1.78 + 2.28 + 2.45 + 2.70 = $10.75M
Enterprise value = 10.75 + 10.28 = $21.03M
```

## Applying it for a client

Match the method to the stage first — using DCF on a pre-revenue company or a Scorecard comparison on a Series C produces a number nobody should trust. Always run at least two methods and present the gap between them explicitly rather than picking whichever number is more flattering; the negotiation is usually in that gap, not in either number alone. Walk investors and founders through the VC method's future-dilution adjustment specifically — it's the step that explains why the "fair" ownership ask looks aggressive on first glance, and skipping it is a common source of avoidable term-sheet conflict.

## Watch-outs

- Berkus and Scorecard are consensus-building anchors for negotiation, not a precise "true value" — don't defend either to two decimal places.
- The VC method is extremely sensitive to two assumptions (exit multiple and required ROI) that are themselves guesses years out — sensitize both before presenting a single number as settled.
- DCF on an early-stage company compounds uncertainty over a long forecast horizon; treat any pre-Series-B DCF output as a sanity check against the VC method, not a standalone answer.
- Comparables and precedent transactions are only as good as how truly comparable the reference companies are — stage, geography, and business model mismatches produce multiples that look precise but aren't relevant.
- Never let the convenient method quietly become "the" valuation without reconciling it against at least one other approach in front of the client.

## Related

- [startup-financial-modeling.md](../finance/startup-financial-modeling.md) — DCF and VC-method terminal values are only as credible as the revenue projections this model produces.
- [cap-tables-dilution.md](../finance/cap-tables-dilution.md) — the pre-money/post-money mechanics computed here are exactly what gets written into the cap table.
- [unit-economics.md](../finance/unit-economics.md) — LTV, CAC payback, and growth efficiency are what an investor is actually underwriting when they set the required ROI in a VC-method calculation.
- [burn-rate-runway.md](../finance/burn-rate-runway.md) — the number of future dilutive rounds assumed in the VC method's dilution adjustment should match the client's actual runway and burn trajectory.
