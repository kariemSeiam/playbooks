---
domain: product-management
concept: Segmentation and Customer Personas
source: sources/product-management/civiconnectors-product-management.pdf.card.md
tags: [segmentation, persona, customer-research, uber-case-study]
---

# Segmentation and Customer Personas

Segmentation is the analytical act of splitting a market into groups that share needs; a customer persona is the creative act of making one of those groups concrete enough that a team can design for it. You need both before writing product requirements — segmentation without a persona stays abstract data nobody designs from; a persona without segmentation underneath it is a guess dressed up as a fact.

## When to use

Do segmentation before you build anything — it's listed as the fourth of the eight product-strategy elements (vision, market analysis, BMC, **persona**, customer lifecycle, metrics/KPIs, roadmap, prioritization), sitting right after the Business Model Canvas defines *who your customer segments are* at a business-model level. Build the persona once a segment is chosen, specifically to make sure feature decisions address a real cluster of pains and motives instead of an assumed "average user" that doesn't actually exist.

## How it works

**Why segmentation matters as a product (not just marketing) exercise:** you need to understand your target customers *before* building the app so you can address their actual pains and motives in your features — segmentation isn't a slide for investors, it's an input to the backlog.

**The four segmentation lenses:**
1. **Demographic** — age, gender, education, social class
2. **Geographic** — region, country, city, population, language
3. **Psychographic** — interests, opinions, personality, values
4. **Behavioural** — purchase pattern and usage pattern, buyer stage, loyalty status

**Building a customer persona** from a chosen segment — the components:
- Demographic info
- Bio (a short narrative — who they are, what their day looks like)
- Goals
- Motivations
- Pain(s)
- Preferred channels
- Usage/purchasing pattern

A persona is not a demographic profile with a stock photo attached — the deck's structure makes clear it needs goals, motivations, and pains filled in with specifics, because those three are what actually drive feature prioritization and messaging decisions later.

## Example

**Uber's customer persona**, worked through every field:
- **Age:** 32, **Gender:** Male, **Occupation:** Marketing Manager, **Location:** Urban area with a busy schedule
- **Bio:** Commutes daily to work using public transportation but seeks a more convenient and comfortable alternative. Values time efficiency and productivity. Enjoys using technology and relies heavily on a smartphone for various tasks.
- **Goals:** Seeks a reliable and efficient transportation solution for daily commuting; values the convenience of door-to-door service without the hassle of driving.
- **Motivation:** Values the flexibility and ease of use Uber provides for various transportation needs; appreciates the cost-effectiveness and time-saving aspects of using Uber regularly.
- **Pains:** Faces challenges with unpredictable public transportation schedules; often needs to travel to meetings at different locations throughout the city; values a seamless and stress-free transportation experience.
- **Preferred Channels:** Mobile app.
- **Purchasing Pattern:** Frequently uses Uber for daily commuting to and from work; prefers UberPOOL for cost-effectiveness and environmental impact; enjoys the comfort of UberX or Uber Comfort for business-related travel.

Note how the pattern-level detail (prefers UberPOOL for cost, UberX for business trips) is a *behavioral segment* insight baked directly into one persona — a reminder that personas often need to capture multiple usage modes rather than a single flat description.

## Applying it for a client

For any client, resist building a persona from internal assumption ("our users are probably busy professionals") — build it from the interview data gathered in the MVP-validation step first (see [mvp-customer-validation.md](mvp-customer-validation.md)), then fill in the persona template. For a clinic client, behavioral segmentation (appointment frequency, chronic vs. acute visits, referral source) is usually more actionable than demographic segmentation (age/gender) because it maps directly to different care pathways and different communication needs. For a branding agency running a rebrand, the persona's "Motivation" and "Pain" fields are the direct source material for messaging and tone — a rebrand built without a filled-out persona is really just a visual refresh with no argument for why the new look should resonate with anyone specific.

## Watch-outs

- One persona per meaningfully distinct segment, not one all-purpose composite — averaging across segments (e.g., merging "cost-sensitive commuter" and "business traveler" into one persona) erases the exact behavioral differences (UberPOOL vs. UberX) that should drive different features or messaging.
- A persona is a hypothesis, not a fact — it should be revisited as usage data and interviews accumulate, the same way a roadmap gets reviewed on a cadence (see [product-roadmap.md](product-roadmap.md)).
- Don't skip straight to persona-building without segmentation — a persona built on a gut-feel target market, without demographic/geographic/psychographic/behavioral analysis underneath it, is just a guess with a name and a stock bio attached.

## Related

- [business-model-canvas.md](../product-management/business-model-canvas.md)
- [customer-value-4cs.md](../product-management/customer-value-4cs.md)
- [mvp-customer-validation.md](../product-management/mvp-customer-validation.md)
