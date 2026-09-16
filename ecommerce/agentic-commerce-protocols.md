---
domain: ecommerce
concept: Agentic commerce protocols — UCP, AP2, and what a merchant must publish to be agent-reachable
source: research — synthesized from ucp.dev specification, Google I/O 2026 Universal Cart announcement, Shopify/ucp-proxy (GitHub), and agentic-commerce protocol coverage (stellagent.ai, agentpedia.codes, universalcommerceprotocol.fr), 2026
tags: [ecommerce, ucp, ap2, agentic-commerce, protocol, checkout, shopify]
---

# Agentic commerce protocols — UCP, AP2, and what a merchant must publish to be agent-reachable

UCP (Universal Commerce Protocol) and AP2 (Agent Payments Protocol) are
open standards, co-developed by Google with Shopify, Etsy, Wayfair,
Target, and Walmart, that let an AI agent (inside Gemini, a Universal
Cart session, or any UCP-compliant client) discover a merchant's catalog,
compare products, and complete a purchase — all without a human ever
navigating to the merchant's website. UCP handles the commerce mechanics
(catalog, cart, checkout, order status); AP2 handles proving,
cryptographically, who authorized a given payment and under what limits.
A merchant that doesn't publish a UCP endpoint isn't just harder to find
by AI agents — increasingly, it is *structurally invisible* to a
transaction flow that never routes through a rendered webpage at all.

## When to use

- A client on Shopify or WooCommerce is asking whether "AI shopping" is
  something to prepare for now or later — the honest answer as of 2026
  is that the protocol layer already exists, has major-platform backing,
  and the integration cost for a standard-platform merchant is measured
  in hours, not months.
- Evaluating why a competitor's product won an agent-mediated comparison
  (a user built a shopping cart via an AI assistant and the competitor's
  item was chosen) despite the client's product being cheaper or
  objectively comparable — the deciding factor is frequently which
  merchant exposed machine-readable attributes the agent could actually
  compare on, not price or marketing.
- Auditing a merchant's technical readiness for the next 12-18 months of
  commerce infrastructure shift, alongside (not instead of) the
  content/schema work in `product-feed-schema-optimization.md`.

## How it works

**The four-layer stack a UCP-compliant merchant actually implements:**

1. **Discovery layer** — a single file at
   `https://yourstore.com/.well-known/ucp.json`, served over HTTPS,
   reachable without authentication (an agent must be able to read it
   *before* it has any credentials). It declares the merchant's identity,
   the real API endpoints for catalog/pricing/checkout/order-status, and
   a `capabilities` block of booleans (does this merchant support
   real-time pricing? returns? subscriptions?) that the generator or
   author must keep honest — the capabilities block is the single field
   most likely to be wrong in an auto-generated manifest, because a
   generator has to *guess* business capabilities a human has to state.
2. **Catalog layer** — the actual product data, exposed via REST or MCP
   (Model Context Protocol), returning structured fields: title,
   description, price range in minor currency units, media, variant
   options, availability, seller identity, and a `checkout_url` per
   variant. This is the layer `product-feed-schema-optimization.md`'s
   schema work feeds directly into — a UCP catalog response and a
   schema.org `Product` block describe largely the same facts through
   different transports.
3. **Transaction layer** — payment and identity compatible with a
   *delegated* buyer, not just a present human one. Two purchase modes
   exist: human-present (an `Intent` and a `Cart` are both signed in real
   time, e.g. "buy this now") and human-not-present delegation (a user
   signs an `Intent Mandate` upfront with price/timing limits — "buy
   concert tickets the moment they go on sale" — and the agent
   autonomously generates the `Cart Mandate` once those conditions are
   met). Agent-pay rails implementing this transaction layer include
   Stripe's Agentic Commerce tooling, Visa Intelligent Commerce, and
   Mastercard Agent Pay — all converging on the same requirement: a
   payment credential that is scoped, revocable, and auditable, not a
   raw stored card number an agent can spend without limit.
4. **Governance layer** — the merchant's retained control: pricing
   policy, eligibility rules, territory restrictions, dispute handling,
   all stated in a machine-readable, versioned form the agent can check
   before completing a transaction on the merchant's behalf.

**What actually changes for a shopper-facing brand, concretely:**

| Stage | Pre-UCP | UCP-enabled |
|---|---|---|
| Discovery | Paid or organic click to a product page | Gemini/an agent surfaces the product directly inside its own answer |
| Comparison | User visits multiple sites manually | Agent compares in the background; the merchant never gets a page view for a comparison it still competed in |
| Checkout | User fills a form on the retailer's site | Agent executes the UCP purchase call autonomously |

The comparison stage is the one worth internalizing hardest: a real,
documented case describes a user building a custom PC through Universal
Cart, where the agent flagged a motherboard/CPU socket mismatch and
substituted a compatible board from a *different* retailer — that
retailer never showed the buyer a homepage, hero banner, or product page
at all. The win came entirely from having the socket-type attribute
structured in a form the agent could read and reason over.

**The practical Shopify path (lowest-friction real implementation).**
`Shopify/ucp-proxy` is a stateless, open-source proxy that translates UCP
calls into a merchant's existing Shopify API — the merchant's store stays
the actual system of record for products, inventory, and pricing; the
proxy is a pure translation layer. Concretely: install a UCP-compatible
app from the Shopify App Store (search "Universal Commerce Agent" or
"UCP"), which auto-generates the `.well-known/ucp.json` manifest and
keeps it current — a merchant should not hand-edit this file once an app
manages it, since manual edits and the app's auto-updates will
eventually conflict.

## Example

A running-shoe retailer on Shopify installs a UCP-compatible app. Its
`/.well-known/ucp.json` now declares `product_search`, `product_filter`,
`cart_operations`, and `checkout` as supported capabilities, with
`catalog_attributes` including `color`, `size`, `brand`, `price`, and
`availability`. A shopper asks an AI assistant "trail running shoes for
marathon training, size 10, under $150" — the assistant's `search_catalog`
call filters directly against these structured attributes (not a fuzzy
text match against the product description) and returns a specific
variant with a direct `checkout_url`, alongside the seller's refund
policy link so the agent can state the return window to the user before
purchase. The retailer's product never had to rank in a traditional
search result at all for this sale to happen.

## Applying it for a client

Distinguish the two audiences correctly before recommending investment:
a merchant on a standard platform (Shopify, WooCommerce) with a
conventional cart-to-payment checkout should use the platform's official
UCP integration path (generated manifest, standard app) — this is
typically an under-an-hour setup and the generator will keep pace with
platform changes. A merchant with genuinely non-standard commerce logic
(B2B quoting, manual order approval, pre-authorization holds,
multi-warehouse partial fulfillment) needs a hand-written or hybrid
manifest, because a generator cannot correctly infer business rules that
only exist in the merchant's own operational process — recommend the
capabilities block specifically be reviewed by a human even when the
rest of the manifest is auto-generated, since that block is where
generators are most likely to overstate or understate what the business
actually supports.

## Watch-outs

- **Shipping a manifest with the `checkout` capability set to `true`
  while the checkout endpoint still points at a staging environment.**
  A documented, real failure mode — always verify every declared
  endpoint resolves in production before considering the manifest live,
  not just that the JSON validates.
- **Treating the UCP manifest as a container for catalog data.** It
  isn't — it's a small, fast discovery pointer to where the real catalog,
  pricing, and checkout endpoints live. A store with tens of thousands of
  SKUs should have a manifest that stays small regardless of catalog
  size; if the manifest itself is growing with the catalog, it's
  structured wrong.
- **Assuming AP2's cryptographic mandate signing protects against all
  manipulation.** It proves *who authorized what payment* — it does not
  validate the *content* a merchant-side agent used to rank or recommend
  a product before that payment was authorized. See
  `agentic-commerce-security.md` for the specific class of attack (the
  Branded Whisper Attack) that exploits exactly this gap.
- **Confusing UCP (Google/Shopify-led, open, multi-retailer) with a
  single vendor's proprietary agent-checkout feature.** UCP's stated
  design goal is interoperability across retailers inside one agent
  session (the Universal Cart use case) — a proprietary single-merchant
  "buy with AI" button is a different, narrower thing and doesn't confer
  the same cross-platform discoverability.

## Related

- **[product-feed-schema-optimization.md](product-feed-schema-optimization.md)**
  — the catalog-data quality layer a UCP endpoint serves from; a
  UCP-compliant endpoint returning thin, incomplete product data is
  still functionally invisible to agent-mediated comparison.
- **[agentic-commerce-security.md](agentic-commerce-security.md)** — the
  attack surface this protocol layer introduces once an LLM is doing the
  ranking/recommendation reasoning inside the transaction flow.
- **`../software-engineering/rest-api-design.md`** — directly applicable
  once implementing the actual UCP catalog/checkout endpoints as a REST
  surface, rather than relying solely on a platform's pre-built proxy.
