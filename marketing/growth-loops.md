---
domain: marketing
concept: Growth Loops
source: research — Brian Balfour, Reforge, "Growth Loops are the New Funnels" (2018)
tags: [growth, loops, acquisition, retention, compounding]
---

# Growth Loops

A growth loop is a closed system where the output of one growth cycle becomes the input to the next — as opposed to a funnel, which is linear and open-ended, requiring fresh outside investment (ad spend, headcount, new content) every time you want more growth. Brian Balfour (Reforge, ex-VP Growth at HubSpot) popularized the concept in 2018, building on earlier viral-loop thinking from Andrew Chen and David Skok, to give growth teams a structural alternative to funnel thinking. A consultant needs it because funnels treat every new customer as an isolated acquisition cost, while loops describe mechanisms where growth becomes structurally cheaper and faster over time as the system runs — the difference between a channel that scales and one that just gets more expensive.

## When to use
- A client's growth is stalling or CAC keeps rising as paid budget increases — a classic symptom of a pure-funnel growth model with no compounding mechanism underneath it
- Designing a new product's core growth mechanism before scaling paid spend behind it
- Evaluating whether a "viral" or "referral" feature is a real loop or just a funnel with a share button bolted on
- Diagnosing why a channel that worked at seed stage stopped scaling at Series A/B
- Prioritizing growth investment across multiple candidate loops by comparing cycle time and output-per-input

## How it works

**Funnel vs. loop, structurally.** A funnel runs Input (spend) → Awareness → Consideration → Conversion → done. The output (a converted customer) does not become new input — to keep growing, the business has to keep injecting new spend or content from outside the system. A loop runs Input → Action → Output → **back into new Input**. Because the system is closed, every user who completes a cycle adds to the pool of inputs available for the next cycle, so growth compounds without a proportional increase in outside spend.

**Anatomy of a loop — three stages:**
1. **Input** — what enters the loop (a piece of content, an invite, a unit of user data).
2. **Action** — what the user or system does with that input (shares it, generates content, uses the product in a way that produces data).
3. **Output** — what's produced (new users, new content, better matching/ranking) — which becomes the Input for the next cycle.

**Four canonical loop types:**

| Loop type | Mechanism | Example |
|---|---|---|
| **Viral loop** | An existing user's action directly exposes the product to new potential users | Dropbox's referral bonus (both sides get storage); a Calendly or Zoom link exposing a non-user to the product as a byproduct of normal use |
| **Content loop** | User- or system-generated content gets indexed/discovered via search or social, drawing new users who generate more content | Pinterest boards surfaced by Google search; Airbnb listing pages; Yelp reviews |
| **Paid loop** | Revenue from converted users is reinvested into paid acquisition for more users | Only closes if LTV clears CAC with enough surplus to fund the next cycle's spend without external capital |
| **Data/network loop** | More usage generates more data, which improves the product, which attracts/retains more users, who generate more data | Waze (more drivers → better traffic data → better routing → more drivers); a marketplace (more supply → better selection → more demand → more supply) |

**Measuring a loop — two numbers matter:**
- **Cycle time** — how long one iteration takes. A viral loop with a one-day cycle compounds far faster than one with a 30-day cycle, even at the same multiplier.
- **Loop coefficient** — how much output each cycle produces relative to input, analogous to a viral k-factor. A coefficient above 1 in isolation is rare and rarely sustained; loops below 1 still compound growth meaningfully when paired with a baseline of external input — they just don't grow entirely on their own.

Balfour's structural point: durable growth companies typically run three to four loops simultaneously, layered (a content loop for top-of-funnel, a network loop for retention/expansion, a paid loop to backfill), rather than depending on one "silver bullet" loop. Loops decay — network saturation, algorithm changes, content going stale — so a growth strategy needs a portfolio, not a single loop run forever.

## Example

PayPal's early referral loop, worked through the anatomy: **Input** — an existing user has a $10-for-you, $10-for-your-friend incentive. **Action** — the user sends or requests money from a friend who isn't yet a PayPal customer, which is something they were already going to do (the ask is embedded in a necessary transaction, not a bolted-on "invite a friend" banner). **Output** — the friend signs up to claim/send the money and collects the bonus, becoming a new existing user with the identical incentive to invite the next person — which becomes the new **Input**. Because the ask was structurally part of using the product rather than an optional extra step, the loop ran on close to a daily cycle time and sustained double-digit daily growth for a stretch — a result a bolted-on referral button rarely achieves, because it depends on a user remembering to act on an incentive rather than the product's core action generating the invite automatically.

## Applying it for a client

Map the client's current growth model onto Input → Action → Output and check literally whether Output feeds back into Input, or dead-ends and next month's growth depends entirely on a fresh injection of spend or content from outside the system. If it dead-ends, it's a funnel, not a loop, and rising CAC as low-hanging paid channels saturate is the predictable result. Then match loop type to product shape: a two-sided marketplace naturally wants a data/network loop, a media or content product naturally wants a content loop — don't force a viral mechanic onto a product with low natural share motivation. Prototype the smallest version of the candidate loop and measure its actual cycle time and coefficient with real cohort data before pouring paid spend into amplifying it; a bad loop scaled by ad spend just becomes an expensive funnel with extra steps.

## Watch-outs
- A referral button or "invite a friend" feature is not automatically a loop — it's only a loop if the resulting new user is structurally likely to perform the same action again, not just a one-time favor asked of existing users.
- Loops decay: network loops saturate as the addressable market fills, content loops decay as search/social algorithms shift or content ages — a growth strategy built on "we found our loop" needs a refresh plan, not permanent faith in one mechanism.
- Fast growth alongside a referral feature doesn't prove the referral loop caused it — isolate and measure the loop's actual contribution (see [attribution-modeling.md](../marketing/attribution-modeling.md)) before reallocating budget toward it.
- Loops work best when designed into the product from the start; retrofitting a loop onto a mature product built around funnel thinking usually means re-architecting the core user action, not adding a feature on top.

## Related
- [product-channel-fit.md](../marketing/product-channel-fit.md) — a loop only compounds if its mechanic actually fits the channel it runs on
- [attribution-modeling.md](../marketing/attribution-modeling.md) — measuring which loop, or which paid channel, actually drove a given conversion
- [content-marketing-peso.md](../marketing/content-marketing-peso.md) — owned and earned media are the substrate a content loop runs on
- [aarrr-pirate-metrics.md](../product-management/aarrr-pirate-metrics.md) — the Referral stage of AARRR is where a viral loop's output re-enters as Acquisition input
