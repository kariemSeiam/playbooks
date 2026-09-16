---
domain: ecommerce
concept: Product feed and schema optimization for Google Shopping, GEO citation, and agentic catalogs simultaneously
source: research — synthesized from Google Merchant Center product data spec, schema.org Product/Offer 2026 requirements (schemavalidator.org, gatilab.com), and UCP catalog minimums (tenten.co, Shopify UCP docs), 2026
tags: [ecommerce, schema-org, json-ld, product-feed, geo, ucp, structured-data]
---

# Product feed and schema optimization for Google Shopping, GEO citation, and agentic catalogs simultaneously

A single, well-structured product page/feed entry can satisfy Google
Shopping's structured-data requirements, an LLM's citation criteria
(`../seo/generative-engine-optimization.md`), and a UCP-compliant AI
shopping agent's catalog minimums at the same time — because all three
consumers are reading the same underlying facts (identity, price,
availability, policy), just through different parsers. Building three
separate content pipelines for these three consumers is the expensive
mistake; one well-structured source with the right fields does all three
jobs.

## When to use

- Setting up or auditing a Shopify/WooCommerce/custom product catalog
  for a client who wants visibility in Google Shopping, wants to be
  recommended by AI shopping assistants (ChatGPT, Gemini, Amazon Rufus),
  and wants to be reachable by emerging AI shopping agents (Universal
  Cart, UCP-based agents) — all three, without three separate projects.
- Diagnosing why a product with a correct price and good photography
  still doesn't show a price snippet in Google Search, or doesn't get
  cited when a customer asks an AI assistant "what's a good X for Y."
- A client's product descriptions are keyword-stuffed for legacy SEO and
  need rewriting — this is the reference for what the *fields themselves*
  should say, distinct from where GEO copywriting principles apply to the
  prose (`../seo/generative-engine-optimization.md` covers the writing
  discipline; this note covers the schema/feed layer specifically).

## How it works

**The four-identifier rule.** `sku`, `gtin13` (or `gtin12`/`gtin8`),
`mpn`, and a nested `brand` object are what let any of the three
consumers resolve a listing as one distinct, verifiable entity rather
than a string of text. Filling all four is the single strongest
legitimacy signal a parser reads — a GTIN specifically is required for
Google's enhanced Merchant Listings experience and improves ranking in
Google Shopping; without one, products remain eligible only for basic
rich results, not the fuller Shopping surface.

**What became effectively mandatory in 2026, not merely recommended:**
`shippingDetails` (via `OfferShippingDetails`) and
`hasMerchantReturnPolicy` are now required by Google for the price
snippet to appear on most retail queries — a listing missing either
still indexes, but competes "naked" against listings that have them.

**A complete, minimal working `Product` JSON-LD block:**

```json
{
  "@context": "https://schema.org",
  "@type": "Product",
  "name": "Ravenback Founder Parka — Men's, Slate",
  "description": "Waterproof 3-layer shell parka with 650-fill recycled down, built for Pacific Northwest winters. Slate, sizes S-XXL, 1.4 kg. Lifetime repair program included.",
  "sku": "RB-FP-SLATE-M",
  "gtin13": "0860009123457",
  "mpn": "FP-2026-SL",
  "brand": { "@type": "Brand", "name": "Ravenback Supply Co." },
  "image": ["https://cdn.example.com/founder-parka-front.jpg"],
  "offers": {
    "@type": "Offer",
    "priceCurrency": "USD",
    "price": "289.00",
    "availability": "https://schema.org/InStock",
    "shippingDetails": {
      "@type": "OfferShippingDetails",
      "shippingRate": { "@type": "MonetaryAmount", "value": "0", "currency": "USD" }
    },
    "hasMerchantReturnPolicy": {
      "@type": "MerchantReturnPolicy",
      "returnPolicyCategory": "https://schema.org/MerchantReturnFiniteReturnWindow",
      "merchantReturnDays": 30
    }
  },
  "aggregateRating": { "@type": "AggregateRating", "ratingValue": "4.7", "reviewCount": "212" }
}
```

**The naming rule that matters more than it looks:** "Ravenback Founder
Parka — Men's, Slate" (brand + model + the variant-identifying attributes
that distinguish this exact SKU) resolves as a distinct entity far more
reliably than "Founder Parka" alone — both to Google's Knowledge Graph
and to an LLM trying to disambiguate which specific product a citation
refers to.

**The description itself: 2-4 citable factual sentences**, not adjective-
led copy. Material, use case, sizing, one genuine differentiator — no
"amazing," "best-in-class" language doing the work a fact should be
doing. This is the schema-layer complement to the prose-writing rule in
`../seo/generative-engine-optimization.md` (specific stated facts extract
cleanly; vague hedged language doesn't).

**Google's Conversational Attributes (2026).** A newer, optional layer
of Merchant Center fields built specifically for AI Overviews/AI Mode,
which fan out a user's question into longer, situational phrasing
("comfortable shoes for road running in winter," not "running shoes 42")
rather than short keyword strings. Practically: up to 30 question-and-
answer pairs per product (each capped at 1,000 characters) covering
what's *not* obvious from the other structured fields, plus a
`related_product` attribute for typed catalog relationships (e.g. a
camera's `required_part` lens, an `accessory` bag).

**UCP catalog minimums, layered on top of the same page.** A UCP-
compliant shopping agent applies its own gate before a product is even
eligible to be included in agent-mediated search results: description
of at least 100 words (under 50 words causes validation errors in
practice), a minimum of 3 product images at 1200×1200px or larger,
accurate SKU/inventory synced with fulfillment, consistent pricing with
no hidden fees, and published policy pages (returns, privacy, terms) the
agent can programmatically verify before completing checkout on a
customer's behalf. See `agentic-commerce-protocols.md` for the full
`/.well-known/ucp.json` manifest this sits underneath.

**The common failure mode across all three consumers, worth naming
once:** a field that exists in the platform's admin (a Shopify metafield,
a WooCommerce custom field) but never reaches the rendered page's JSON-LD
is invisible to all three — Google, an LLM's retrieval crawler, and a UCP
agent all read the rendered structured data, not the admin panel. The
observed gap on Shopify specifically: `gtin13` missing in roughly 70%+ of
stores audited, `priceValidUntil` missing in roughly 80%, because no
Shopify theme emits either by default.

## Example

A Shopify store sells a $290 winter parka with excellent photography and
a well-written description, but: no `gtin13` in the theme's emitted
schema, no `hasMerchantReturnPolicy`, and a 35-word description. Result
across all three consumers simultaneously — Google Shopping shows the
listing without a price snippet or ratings (missing `aggregateRating`
and the two now-mandatory fields), an AI assistant asked "what's a good
waterproof parka for Pacific Northwest winters" doesn't cite the product
because the 35-word description doesn't clear the citable-passage bar,
and a UCP shopping agent's catalog-search call excludes the product
entirely because it fails the 100-word minimum. The fix is a single
content pass — extending the description to 3-4 factual sentences,
adding the GTIN from the manufacturer, and adding the shipping/return
schema blocks — that resolves all three failures at once, because they
share the same root cause.

## Applying it for a client

Run a single audit pass per product against three checklists at once
rather than three separate audits: (1) the four identifiers plus
shippingDetails/hasMerchantReturnPolicy for Google eligibility, (2) a
2-4 sentence factual description plus FAQ pairs for GEO citation
eligibility, (3) 100+ word description, 3+ images at 1200px+, and
published policy pages for UCP agent eligibility. In practice the first
and third overlap heavily (both need a real description length and
complete identifiers) — fixing for one fixes most of the other for free,
which is the efficiency argument for treating this as one system rather
than three client deliverables.

## Watch-outs

- **Fixing schema in a page's `<head>` without verifying it survives to
  the rendered DOM.** Some page builders and apps inject JSON-LD via
  client-side JavaScript that a crawler without a JS-execution step never
  sees — verify with Google's Rich Results Test and by viewing the actual
  page source, not just the admin configuration.
- **Keyword-stuffing the description to "cover more search terms."**
  This actively hurts GEO citation odds (vague, padded language extracts
  poorly) and UCP eligibility is about descriptive completeness, not
  keyword density — the incentives point the same direction: write fewer,
  more specific, more factual sentences.
- **Treating Conversational Attributes as required.** They're optional
  and additive; a product missing them is still fully eligible for
  standard Shopping and GEO citation — prioritize the four identifiers
  and the two now-mandatory shipping/return fields first.
- **Assuming one CMS's auto-generated schema is complete.** Shopify emits
  basic Product schema automatically but omits `aggregateRating` by
  default (a review app like Judge.me or Loox is what actually injects
  it) and frequently omits `gtin13` and `priceValidUntil` — verify by
  reading the actual rendered source, per the audit method above, rather
  than assuming platform defaults are sufficient.

## Related

- **`../seo/generative-engine-optimization.md`** — the general
  prose-writing discipline (specific stated facts over hedged language,
  40-60 word citable passages) this note's description-writing guidance
  applies at the schema-field level specifically.
- **[agentic-commerce-protocols.md](agentic-commerce-protocols.md)** —
  the UCP manifest and endpoint layer this note's catalog-minimums
  section sits directly underneath.
- **[platform-ranking-algorithms.md](platform-ranking-algorithms.md)** —
  once discoverable, this is what actually determines organic
  distribution on TikTok Shop and Amazon specifically.
