---
domain: strategy
concept: Wardley Mapping
source: 'research — Simon Wardley, *Wardley Maps: Topographical Intelligence in Business* (2016, published free online)'
tags: [situational-awareness, evolution, value-chain, strategy, mapping]
---

# Wardley Mapping

Wardley mapping is a visual technique for building genuine situational awareness of a business or system by plotting every component of a value chain against two axes: how visible it is to the end user, and how evolved or commoditized it is, from novel invention to industrial commodity. Simon Wardley developed it over roughly a decade of practitioner work, including at Fotango and Canonical, and published the method free online rather than sell it as a proprietary framework. A consultant needs it because most strategy tools (SWOT, the BCG matrix, Porter's Five Forces) describe a business's position with no reference to *why* components will change over time — Wardley maps make the evolutionary dynamic explicit and falsifiable, so build/buy and investment decisions have a reason attached, not just a snapshot.

## When to use

- Strategy conversations keep talking past each other because there is no shared visual of what the value chain actually is and how mature each part is
- Build-vs-buy-vs-outsource decisions for any specific component (this directly informs the logic in [ai-build-vs-buy.md](ai-build-vs-buy.md))
- Anticipating disruption — identifying which parts of the value chain are about to commoditize (treat as utilities, buy) versus which are still genuinely novel (the real differentiator)
- Portfolio or roadmap prioritization across many components, when it's unclear which deserve custom investment versus off-the-shelf treatment
- Competitive analysis that goes beyond "what do they offer" to "where is their value chain more or less evolved than ours, and where's the exploitable gap"

## How it works

**Two axes.**

- **Y-axis — value chain (visibility).** How directly visible a component is to the end user, from the user's need at the top down through progressively more invisible, foundational components below. Built by repeatedly asking "what does this component need in order to exist or function?" and placing that dependency below it.
- **X-axis — evolution.** How commoditized a component is, moving left to right through four stages:

| Stage | Character | Example |
|---|---|---|
| **Genesis** | Novel, poorly understood, rare, actively being invented | Early-stage quantum computing research |
| **Custom-built** | Individually made, uncommon, still rapidly changing, high uncertainty | Bespoke early web servers (mid-1990s) |
| **Product (+rental)** | Becoming a defined product, differentiation between vendors, growing but incomplete standardization | Branded servers with distinct feature sets |
| **Commodity (+utility)** | Standardized, widely available, undifferentiated, often consumed as a metered utility | Electricity, cloud compute (AWS EC2), water |

Every component evolves left to right over time, driven by supply-and-demand competition and the diffusion of practice — nothing stays in Genesis or Custom-built forever, and nothing naturally moves right to left. This directionality is what makes the map predictive, not just descriptive.

**Building a map — the process:**

1. Anchor on the user and their need at the top
2. Build the value chain downward: for each component, ask what it needs beneath it to function, and place that dependency below
3. Position every component on the X-axis by its actual evolutionary stage, not where you'd like it to be
4. Look for mismatches: components mapped far right (commodity) but still being custom-built in-house are usually wasted effort; components on the left (genesis/custom) that are core to differentiation are where real investment belongs
5. Apply "climate patterns" — Wardley's term for recurring market forces (everything inexorably commoditizes, componentization enables higher-order systems built on top) — to anticipate what the map will look like in one to three years, not just today

**Doctrine.** Wardley also codifies generic good practices ("universal doctrine" — know your users, use a common language, focus on high cohesion and loose coupling, remove duplication and bias) that apply regardless of the specific map. Doctrine sits below strategic "gameplay" — deliberate moves like exploiting a competitor's inertia — which itself sits below context-specific strategy.

## Example

A retailer maps its e-commerce checkout flow. User need at the top: "buy the product." Below it: checkout UI (custom-built — still differentiated, a genuine UX battleground) → payment processing (product/rental stage — several vendors with differentiated features, not yet a pure utility) → cloud hosting (commodity — AWS/GCP/Azure, fully utility, buy don't build) → electricity (commodity/utility, not even a decision anymore). The map immediately reveals a common mistake: a team that has built its own in-house cloud hosting layer at the commodity stage is burning engineering effort on a solved, undifferentiated problem, while possibly under-investing in the checkout UI, where genuine differentiation is still available.

## Applying it for a client

Run mapping as a live whiteboard session with the people who actually know each component's maturity — engineering, product, ops — since a single strategist guessing at evolution stages produces a fictional map. Once mapped, run the build-vs-buy conversation component by component using evolution stage as the primary signal: genesis or custom-built and core to differentiation → build; product or commodity and non-differentiating → buy, outsource, or treat as a utility (the exact logic [ai-build-vs-buy.md](ai-build-vs-buy.md) applies specifically to AI capabilities). Revisit the map periodically — components migrate rightward over time, so a map is a snapshot, not a permanent artifact.

## Watch-outs

- A map built without direct input from people who actually operate each component becomes a plausible-looking fiction — evolution-stage judgments need real domain knowledge, not a consultant's best guess
- The map only pays off if it changes a decision — a beautifully drawn map filed away without an attached build/buy/kill decision is wasted effort
- People new to the technique often conflate the Y-axis (visibility to user) with importance or value — a component can be invisible to the user (a database) and still be strategically critical; visibility and strategic importance are different questions
- Evolution is not a value judgment on quality — a genesis-stage component isn't "worse" than a commodity one, it's earlier on a maturity curve; the map's job is to show where investment logic differs, not to rank goodness
- Maps decay — treat as a living document reviewed on a regular cadence, quarterly or semi-annually in fast-moving spaces, not a one-time strategy artifact

## Related

- [value-chain.md](../operations/value-chain.md) — Wardley's Y-axis is a value chain in the same sense as Porter's; this note adds the evolutionary X-axis that a static value chain lacks
- [ai-build-vs-buy.md](../strategy/ai-build-vs-buy.md) — the same genesis-to-commodity evolution logic directly justifies that note's staged build/buy default
- [competitor-analysis-matrix.md](../marketing/competitor-analysis-matrix.md) — mapping a competitor's value chain onto the same evolution axes surfaces where they're over- or under-invested relative to you
