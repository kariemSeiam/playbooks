# E-commerce — declarative field notes, the agentic-commerce layer

Same shape every declarative field here uses
(`../software-engineering/README.md` documents it canonically): atomic
notes, one topic each, 7-part shape. Its own top-level folder rather than
a subfolder of `seo/` or `marketing/` because it spans a distinct
operating stack — market/payment-model economics, platform ranking
algorithms with real financial stakes, product-data machine-readability,
and the emerging agent-to-agent transaction layer — none of which reduces
cleanly to "marketing knowledge" or "being cited in an answer." Where a
note here needs generic GEO mechanics, it links to
`../seo/generative-engine-optimization.md` rather than restating it —
this folder covers what's specific to *transacting*, not to *being
found* in general.

## Notes

- **[market-selection-cod-economics.md](market-selection-cod-economics.md)** — how to
  choose a launch country by real unit economics (AOV, COD delivery
  rate, ad CPM) instead of "biggest market" instinct — Morocco vs Gulf vs
  US/UK compared on the numbers that actually decide first-90-day
  survival.
- **[platform-ranking-algorithms.md](platform-ranking-algorithms.md)** — the
  commerce-specific ranking engines a seller answers to day to day:
  TikTok Shop's Coral (commerce-quality score), Amazon's A10/COSMO
  (post-purchase signals over historical sales), and the common pattern
  underneath both — operational reality outranks marketing polish.
- **[product-feed-schema-optimization.md](product-feed-schema-optimization.md)** —
  making a single product page/feed entry legible to Google Shopping,
  a GEO-citing LLM, and a UCP shopping agent simultaneously, without
  three separate content pipelines. Builds on
  `../seo/generative-engine-optimization.md` rather than repeating it.
- **[agentic-commerce-protocols.md](agentic-commerce-protocols.md)** — UCP
  (Universal Commerce Protocol) and AP2, the open standards letting an AI
  agent discover a merchant, browse a catalog, and complete checkout
  without a human clicking through a website — what a merchant actually
  has to publish and support to be reachable this way.
- **[agentic-commerce-security.md](agentic-commerce-security.md)** — prompt
  injection targeting the merchant-agent and shopping-agent layer
  specifically (the Branded Whisper Attack and its relatives): how
  untrusted product-listing text becomes an attack surface once an LLM is
  the one reading and ranking it, and the concrete sanitization/isolation
  defenses that hold up against it.

## Related

- **`../seo/generative-engine-optimization.md`** — the general discipline
  of being cited in an LLM's synthesized answer; this folder's
  product-feed note builds directly on it for the commerce-specific
  case.
- **`../seo/fundamentals.md`** — the three classic SEO pillars every note
  here still assumes as a floor; agentic commerce doesn't replace
  crawlability and on-page relevance, it adds a layer on top of them.
- **`../software-engineering/rest-api-design.md`** — relevant once
  implementing the UCP endpoints (`agentic-commerce-protocols.md`)
  described here as an actual API surface.

## The one rule that overrides all of this

A project's own stated convention always wins over this playbook's
defaults — same as every other playbook here.
