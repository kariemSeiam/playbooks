---
domain: ecommerce
concept: Market selection by COD/AOV economics, not market size
source: research — synthesized from 2026 dropshipping/COD market data (CODRocket, NicheDropshipping, Grand View Research, ecdb.com AOV rankings), 2026
tags: [ecommerce, dropshipping, market-selection, cod, aov, unit-economics]
---

# Market selection by COD/AOV economics, not market size

Picking a launch country for a dropshipping or COD e-commerce operation
by "biggest market" or "most talked-about" instinct (US, UAE) instead of
by the numbers that actually decide whether the first 90 days survive:
average order value (AOV), cash-on-delivery (COD) delivery/completion
rate, and ad CPM in that market. These three numbers interact — a high-
AOV market is worthless if ad costs eat the margin before delivery, and a
low-CPM market is worthless if COD completion is so low that half of
placed orders never convert to cash in hand.

## When to use

- A client or founder is choosing a first country to launch a COD or
  dropshipping storefront in, and the instinct is "the US/UK because
  it's the biggest market" without having run the unit-economics math.
- Diagnosing why a store profitable in one country is unprofitable in
  another with an identical product and identical ad creative — the gap
  is usually AOV × completion rate × (1 − CPM-driven CAC), not creative
  quality.
- Evaluating whether to expand into a second market before the first is
  actually profitable — this framework is also the checklist for whether
  that second market is a real opportunity or a distraction.

## How it works

Three numbers, multiplied together, decide whether a market is
survivable for a new operator with a limited ad budget:

1. **AOV (average order value)** — what a market actually spends per
   order. Global e-commerce AOV averages roughly $150 (late 2025), but
   the spread by country is wide: Switzerland tops the world at ~$239,
   the US sits at ~$183, while COD-first Gulf/MENA markets (Morocco,
   Egypt) run far lower per order but at a fraction of the ad cost.
2. **COD completion/delivery rate** — the percentage of COD orders that
   are actually accepted and paid for at the door, not just placed. This
   varies enormously by country's courier maturity and customer
   familiarity with online buying: UAE leads globally at ~84%, Saudi
   Arabia ~82%, Kuwait ~81%, while newer COD markets run lower (Morocco
   ~73%) but climbing. A market with a high AOV and low completion rate
   can underperform a low-AOV, high-completion one on delivered revenue.
3. **Ad CPM (cost per thousand impressions)** — what it costs to reach a
   customer in that market on Meta/TikTok. Gulf markets (UAE, KSA, Qatar)
   run 4-5× the CPM of Morocco or other lower-competition MENA markets
   for comparable reach, because more established operators already
   compete there.

**The operator-tier split this produces in practice:**

- **Low ad budget, new operator:** a market with the *lowest combined
  cost* (CPM × ad-spend-to-conversion), even at a lower AOV. Morocco is
  the frequently-cited 2026 example: 73% COD delivery rate, a mature
  Shopify-integrated courier network (Sendit, Speedaf), and reported
  1.8-2.4× ROAS for new stores in their first three months — a
  materially friendlier starting curve than a high-CPM Gulf launch on the
  same budget.
- **Higher ad budget (roughly 500 USD/month+):** a market where AOV is
  roughly double (UAE/KSA) can absorb the 4-5× higher CPM, because the
  per-order economics compensate for the acquisition cost. This tier is
  where "biggest market" instinct starts being defensible again — but
  only once the budget genuinely supports the higher CAC that market
  demands.
- **Card-first markets (US, UK, Western Europe):** COD is close to
  pointless here — card penetration runs 90%+ and offering COD in a
  market that doesn't expect it measurably drops conversion (documented
  at roughly a third of normal checkout conversion when COD is offered
  where it isn't the local norm). These markets are a different playbook
  entirely (card checkout, higher AOV ceiling, much higher competition
  and CPM) — see `platform-ranking-algorithms.md` for the operational
  bar (fulfillment SLA, return rate) that governs discovery there.

## Example

A new operator with a $150/month ad budget is deciding between launching
a COD storefront targeting UAE or Morocco with the same product (a $25
landed-cost accessory). UAE math: AOV ~$70, but CPM roughly 4-5× Morocco's
means the same $150 buys a fraction of the reach, and the 84% COD
completion rate doesn't offset the acquisition cost gap at this budget
tier. Morocco math: AOV lower (~$25-30) but CPM low enough that the same
$150 buys meaningfully more reach, 73% COD completion is workable, and
the reported 1.8-2.4× ROAS in the first three months for new Morocco
launches gives this operator a realistic path to profitability before
the budget runs out. The conclusion isn't "Morocco is always better" —
it's that at *this specific budget tier*, the combined-cost math favors
it, and the same operator revisiting the decision after $500+/month
budget is available should re-run the comparison, because the UAE
math changes favorably at that tier.

## Applying it for a client

Before recommending a launch market, ask for (or estimate from public
sources) the three numbers for every market under consideration — AOV,
COD completion rate, ad CPM — and multiply them into a rough "cost to
land one delivered order" figure per market, not per impression. Present
market selection as a function of the client's actual ad budget tier,
not a single "best market" answer: the right market for a $100/month
operator and a $2,000/month operator are legitimately different
countries, and recommending the same market to both is a category error.
Revisit the recommendation every time the budget tier changes materially
— this isn't a one-time decision.

## Watch-outs

- **Confusing "biggest e-commerce market" with "best market for a new,
  budget-constrained operator."** The US being a $1.23 trillion market
  says nothing about whether a $150/month ad budget can compete there;
  those are different questions entirely.
- **Offering COD in a card-first market (or vice versa) out of habit.**
  This isn't a minor conversion tweak — it's close to a category error
  that can cut conversion to a third of normal in the wrong direction.
- **Ignoring courier/logistics maturity as a silent multiplier.** A
  market with a high theoretical AOV but immature COD courier
  infrastructure (frequent failed deliveries, long transit times) will
  underperform its AOV number in practice — the completion-rate figure
  exists specifically to catch this.
- **Treating this as a one-time decision.** Ad CPMs, COD completion
  rates, and competitive density all shift year over year (Gulf CPMs in
  particular have been rising as more operators enter) — re-run the
  comparison before scaling spend materially, not just at launch.

## Related

- **[platform-ranking-algorithms.md](platform-ranking-algorithms.md)** —
  once a market is chosen, this is the operational bar (fulfillment
  speed, return rate) that determines whether a product actually gets
  algorithmic distribution in that market's dominant sales channel.
- **[product-feed-schema-optimization.md](product-feed-schema-optimization.md)**
  — market-specific currency, shipping, and return-policy fields that
  must be correct per market in the product feed itself.
