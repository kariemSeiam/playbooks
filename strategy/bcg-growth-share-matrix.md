---
domain: strategy
concept: BCG Growth-Share Matrix
source: research — Henderson, B.D. (1970), "The Product Portfolio," Boston Consulting Group perspective
tags: [portfolio, resource-allocation, growth, market-share]
---

# BCG Growth-Share Matrix

The Growth-Share Matrix, created by Bruce Henderson at Boston Consulting Group in 1970, was the first widely adopted tool for treating a multi-product or multi-business-unit company as a *portfolio* to be balanced — rather than a set of businesses each judged only on its own P&L. It plots every business unit or product line on two axes — market growth rate and relative market share — and uses the position to decide whether a business should be funded, harvested, or exited. A consultant needs it because it remains the fastest way to force a client with more than one business line into a single conversation about where cash is actually being generated versus where it's being consumed, and whether that allocation is deliberate or just historical inertia.

## When to use

- A multi-product or multi-division client has never explicitly compared business units on the same two axes and is allocating capital by habit, politics, or whoever asks loudest, rather than by portfolio logic.
- A client's overall growth has stalled and no one can say which specific units are dragging or driving it.
- Preparing for a divestment or discontinuation conversation — the matrix gives a structural, less personal reason ("this is a Dog: low growth, low share, structurally unlikely to fund itself") than a bottom-up P&L argument alone.
- A cash-generating legacy business needs to be explicitly identified and protected from over-investment, so its cash can fund newer bets instead.
- Early portfolio triage before a deeper tool like [ge-mckinsey-nine-box.md](ge-mckinsey-nine-box.md) — BCG is the fast two-variable pass; GE/McKinsey is the slower, more nuanced multi-variable pass.

## How it works

### The two axes

- **Market growth rate** (vertical) — the growth rate of the *industry* the business unit competes in, typically split at a threshold (often ~10%, adjustable to context) into "high growth" and "low growth." This is a market characteristic, not a reflection of the business unit's own performance.
- **Relative market share** (horizontal) — the business unit's market share *relative to its largest competitor* (not absolute share), typically expressed as a ratio (e.g., a unit with 20% share in a market where the leader has 40% has 0.5x relative share). Split into "high" (above 1.0x, i.e., the unit is the market leader) and "low" (below 1.0x).

### The four quadrants

| | High relative share | Low relative share |
|---|---|---|
| **High market growth** | **Stars** | **Question Marks** |
| **Low market growth** | **Cash Cows** | **Dogs** |

- **Stars** — high growth, high share. Market leaders in growing markets. Typically require heavy continued investment to maintain share and keep pace with market growth, but are the future cash cows if they can sustain leadership until the market matures. Cash-neutral to cash-consuming in the near term, cash-generative later.
- **Cash Cows** — low growth, high share. Market leaders in mature/slow markets. Require relatively little reinvestment (the market isn't expanding, so defending share is cheaper than growing into a market), and their leadership position typically produces experience-curve cost advantages — the classic mechanism for generating surplus cash to fund Stars and selected Question Marks elsewhere in the portfolio.
- **Question Marks** (also "Problem Children") — high growth, low share. Consuming cash to keep pace with a fast-growing market, but without leadership position, uncertain whether investment will convert them into Stars or whether they'll fade into Dogs as the market matures. The genuinely strategic decision quadrant — invest hard to try to win leadership, or exit before more cash is sunk.
- **Dogs** — low growth, low share. Neither generating meaningful cash nor offering a growth story; the classic recommendation is divest, minimize investment, or hold only if it serves a defensive/strategic purpose (e.g., blocking a competitor, completing a product line a bigger customer requires).

### The intended cash logic

The matrix's real purpose, more than the labels themselves, is a *cash-flow balancing act* across the whole portfolio: Cash Cows fund Stars (which need investment now to be tomorrow's Cash Cows) and selectively fund the most promising Question Marks (to try converting them into Stars before the market matures around a competitor instead). Dogs are typically starved of further investment and eventually divested, harvested for residual cash, or held only for a specific strategic reason. A healthy portfolio, in BCG's original logic, has enough Cash Cows to fund enough Stars and Question Marks to replace the Cash Cows as they eventually mature into Dogs — an explicitly cyclical, self-renewing view of a corporate portfolio.

## Example

**A consumer packaged-goods company's product portfolio, plotted on the matrix:**

- **Cash Cow:** The company's original, decades-old flagship detergent brand — category growth is now roughly flat, but the brand holds dominant share and throws off reliable annual cash with minimal marketing spend needed to defend it.
- **Star:** A recently launched eco-friendly cleaning line in a fast-growing "sustainable household products" category, where the company already holds the leading share — still requires continued marketing and capacity investment to keep pace with category growth, but is on track to become the next Cash Cow once that category matures.
- **Question Mark:** A new entry into the fast-growing personal-care subscription-box category, where the company has only a small share behind two better-known competitors — genuinely undecided whether continued investment converts this into a Star or whether it should be exited before more capital is committed.
- **Dog:** An old air-freshener line in a flat, declining category where the company holds a small, non-leading share — generates little cash, requires disproportionate management attention relative to its contribution, and is a divestment or discontinuation candidate.

The portfolio decision this analysis drives: use the detergent Cash Cow's surplus cash to fund the eco-friendly Star's continued growth investment and to fund a decisive (rather than half-hearted) push on the subscription-box Question Mark, while committing to exit or minimally maintain the air-freshener Dog rather than letting it keep consuming management time proportional to a bigger, more promising line.

## Applying it for a client

Get the two inputs right before trusting the plot — market growth rate needs a real external data source (industry reports, not the client's internal sales trend), and relative market share needs an honest competitor benchmark, not the client's self-perception of "we're a major player." A common failure mode is a client insisting a unit is a Star when the actual relative-share math (against the true market leader, not against a rounding-error competitor) puts it in Question Marks — do the arithmetic explicitly rather than accepting the label the client already prefers. Once plotted, walk the client through the cash-flow story across the whole matrix, not quadrant by quadrant in isolation — the value of the tool is forcing the conversation "your Cash Cow's cash is currently going where, and should some of it be redirected to your Star instead of sitting in the Cash Cow's own marketing budget out of habit." Be direct about Dogs: this is the quadrant clients resist acting on most, often for organizational/emotional reasons (a founder's first product, a unit with tenured staff), and the consultant's job is to make the cash-opportunity-cost argument explicit rather than let inertia decide.

## Watch-outs

- The matrix is a snapshot with only two variables — it says nothing about *why* a unit has low share (bad execution vs. a genuinely tough competitive structure) or whether the market-growth threshold split is meaningful for this specific industry; use [porters-five-forces.md](porters-five-forces.md) alongside it to understand the *why* behind the position, and [ge-mckinsey-nine-box.md](ge-mckinsey-nine-box.md) when two variables aren't enough.
- "Relative" market share is frequently computed wrong in practice — clients report absolute share (their % of the whole market) rather than share relative to the largest competitor; the whole horizontal-axis logic breaks if this isn't corrected.
- The prescriptive labels (fund Stars, milk Cash Cows, divest Dogs) are guidelines, not laws — a Dog with strategic value (blocking a competitor, serving a key account, completing a product line) can be worth holding at a cash-neutral cost that never shows up as "success" in this two-variable view.
- Cash Cows can be starved to death by over-application of the "milk it" logic — a Cash Cow's market can shift (technology, new entrant) and a business unit denied all reinvestment for years may lose the very leadership position that made it a Cash Cow in the first place.
- The matrix assumes market share is causally linked to profitability via the experience curve — that link is empirically real in some industries (manufacturing, especially) and much weaker in others (many services, fast-changing tech); don't apply the tool mechanically where the underlying cost-experience assumption doesn't hold.

## Related

- [ge-mckinsey-nine-box.md](../strategy/ge-mckinsey-nine-box.md) — a more nuanced multi-variable portfolio tool for when growth-share alone doesn't capture enough.
- [three-horizons-of-growth.md](../strategy/three-horizons-of-growth.md) — a time-horizon view of the same underlying idea (balance today's cash generators against tomorrow's growth bets).
- [porters-five-forces.md](../strategy/porters-five-forces.md) — explains *why* a unit's market has the growth rate and competitive intensity it does.
- [cash-flow.md](../finance/cash-flow.md) — the cash mechanics the matrix's fund-Stars-from-Cows logic depends on.
