---
domain: ecommerce
concept: GEO copywriting framework — query fan-out, P-A-S-B structure, and a documented before/after case
source: research — synthesized from query fan-out mechanics (acromatico.com, thinkprofits.com, claudio-novaglio.com, algoblueprints.com, 2026), the P-A-S-B framework (stormy.ai 2026 Shopify GEO playbook), Semji's GEO product-page pillars, and a documented before/after case study (dev.to/ndabene), 2026
tags: [ecommerce, geo, copywriting, query-fan-out, product-description, case-study]
---

# GEO copywriting framework — query fan-out, P-A-S-B structure, and a documented before/after case

Writing product copy for generative engines requires answering the
*sub-questions* a real buyer's query decomposes into (query fan-out),
not just the head-term keyword classic SEO targeted — because AI Mode,
ChatGPT, and Perplexity retrieve and cite passages against those
sub-questions individually, not against the literal phrase typed. This
note gives the mechanism (fan-out), the sentence-level structure
(P-A-S-B) that produces citable passages, and a real, numbers-backed
before/after case showing the combined effect. It sits directly beneath
`../seo/generative-engine-optimization.md`'s general GEO principles and
`product-feed-schema-optimization.md`'s schema layer — this note is
specifically about what the *prose* should say.

## When to use

- Rewriting a product description, comparison page, or buying guide that
  ranks acceptably in traditional Google search but is never mentioned
  when the same target customer asks an AI assistant the equivalent
  question — the diagnostic gap `generative-engine-optimization.md`
  already names, this note supplies the concrete writing fix.
- Planning content for a new product launch where the goal explicitly
  includes AI-assistant visibility (ChatGPT Shopping, Gemini/AI Mode,
  Perplexity, Amazon Rufus) alongside traditional search and paid
  channels.
- Auditing an existing catalog at scale (500+ SKUs) to decide which
  products get manual editorial attention versus AI-bulk-generated
  copy — the "Review by Exception" prioritization below is the practical
  answer.

## How it works

**Query fan-out, applied to product copy specifically.** The core
mechanism (a generative engine decomposes a question into sub-queries
and retrieves per sub-query) is already documented in
`../seo/generative-engine-optimization.md` — read that first if it's
unfamiliar. What's specific to product copywriting: "Best non-toxic
all-purpose cleaner for a home with a baby and a dog" fans out into
distinct purchase-decision nodes — is it actually safe (ingredients),
concentrate vs. ready-to-use (cost/waste trade-off), cost per use,
third-party certifications, and what real buyers report. None of these
five nodes is the head keyword "all-purpose cleaner" — the fan-out lives
entirely in the adjacent purchase decisions a product page rarely
addresses explicitly. Two measurements worth having on hand for a
client conversation: AI citations match a traditional Google top-10
result only 7-12% of the time (the two are citing for different reasons
entirely), and only about 27% of sub-queries stay consistent across
repeated searches of the same head question — so the practical target is
covering the full semantic space of likely purchase-decision
sub-questions, not identifying and targeting one fixed set.

**Practical fan-out mapping, per product/topic:**

1. Start from the real buyer question, phrased the way a person actually
   types it into an AI assistant (15-20 words, conversational — not a
   3-word keyword string).
2. List every purchase decision a buyer must resolve before they can act
   on that question (safety, cost-per-use, fit-for-scenario, social
   proof — not the product category itself).
3. Build a dedicated, well-structured, self-contained section for each
   resolved decision — each one independently citable, because the
   engine retrieves and cites at the passage level, not the document
   level.
4. Reverse-engineer gaps: ask ChatGPT or Perplexity the target head
   query, read the inline citations, and identify which sub-question
   each cited source is actually answering — the sub-questions your
   content doesn't yet cover are the content plan.

**P-A-S-B — the sentence-level structure that produces citable prose.**
Problem → Agitation → Solution → Benefit, the 2026 standard structure
specifically because it front-loads a *specific, extractable claim*
rather than adjective-led marketing copy. Worked example: instead of
"This is a lightweight jacket" (nothing here is independently citable —
no comparison, no number, no context), P-A-S-B produces: *"Hate feeling
weighed down by bulky winter coats? Traditional parkas make commuting a
sweaty nightmare. Our Aero-Lite Shell provides sub-zero protection at
half the weight. You stay warm without the bulk, pack it into a
briefcase, and never worry about overheating on the train."* Each clause
is independently extractable and specific (a comparison, a use case, a
concrete outcome) — this is the same underlying principle as
`product-feed-schema-optimization.md`'s "2-4 citable factual sentences"
schema-description rule, applied at full copywriting length.

**The five editorial pillars for a full GEO-optimized product page**
(beyond the head description):

1. **Scenario-based description** — "30L backpack suited to a 3-day
   mountain hike, with a hydration compartment and ventilated back
   panel" instead of "30L backpack." Places the product inside a real
   usage situation a fan-out sub-query would ask about.
2. **A built-in FAQ, 5-10 questions** — targeting the actual
   conversational objections a buyer raises before purchase ("Is this
   suitable for beginners?", "What is the average lifespan?"), each
   answered directly and factually, not defensively.
3. **Review/credibility signals** — AI engines weight review volume
   (roughly 100+ as a confidence threshold) and average rating (4.5+ as
   a strong signal) when assessing whether to trust a recommendation;
   detailed, scenario-specific reviews carry more signal than generic
   star-only ratings.
4. **Descriptive alt tags and short demo video** — multimodal engines
   parse images and video directly; an alt tag should describe precisely
   what's shown ("Front view of the black 30L backpack with adjustable
   straps and zippered front pocket"), not "backpack image 1."
5. **schema.org markup** (`Product`, `Offer`, `AggregateRating`) — the
   machine-readable layer the prose sits on top of; see
   `product-feed-schema-optimization.md` for the field-level detail.

**Length guidance:** 300-800 words of editorial content beyond the
structured spec table, scaled to product complexity — 300-500 for a
simple/standard product, 600-800 for a technical or premium one
justifying comparisons and deeper use-case coverage.

## Example

A documented case (a technical trail-running shoe on a mid-market
e-commerce site) went from an 80-word, pure-spec description with zero
third-party mentions and 4 short reviews to a fully GEO-restructured
page: a semantically enriched title, an "expert summary" opening
paragraph with specific verifiable claims ("tested over 200 km of Alpine
trails," "30-50% cheaper than comparable models"), a "who is this for"
section, a technical-spec table reframed around real-world effect rather
than raw numbers, a 3-question FAQ, and a reviews block with attributed,
scenario-specific quotes. The team also built a supporting "GEO cluster"
of three linked articles (a buying guide, an honest head-to-head
comparison against two named competitors, and a long-term field-test
report) and seeded external authority signals — sending the product to
independent trail-running blogs, answering relevant Reddit/Quora
questions with factual mentions, and using the exact same product name
and key descriptors ("TrailForce X1," "technical terrain," "Vibram
MegaGrip sole") consistently across every external mention.

**Measured results at D+60:**

| Metric | Before | After (D+60) | Change |
|---|---|---|---|
| Total AI mentions (of 45 test combinations) | 0 | 14 | new channel |
| Perplexity mentions (of 15 test queries) | 0 | 7 | new channel |
| ChatGPT mentions (of 15) | 0 | 4 | new channel |
| Gemini mentions (of 15) | 0 | 3 | new channel |
| Product page traffic/month | 120 | 185 | +54% |
| Traffic from AI assistants | 0 | 64 combined | new channel |
| Support-content (blog) traffic | 30 | 210 | +600% |
| Units sold/month | 4 | 7 | +75% |
| Traditional Google position | 8 | 5 | +3 positions |

The traditional-SEO-position improvement alongside the AI-citation gain
is the finding worth internalizing: GEO and classic SEO are not
competing budgets — the same content depth, structured data, and
external authority-building that earns AI citations also measurably
improved the traditional ranking, because both systems ultimately reward
the same underlying substance (specific, sourced, well-structured,
externally corroborated content).

## Applying it for a client

Run the reverse-engineering step first, before writing anything: ask the
target AI assistants the client's actual candidate buyer questions and
record whether the client is cited, a named competitor is cited, or
neither. This is the GEO equivalent of a rank-tracking baseline
(`../seo/generative-engine-optimization.md` names this same diagnostic).
For a catalog of any real size, apply "Review by Exception" —
AI-generate drafts for the full catalog using the P-A-S-B structure and
a rich input brief (real specs, real audience, one brand-story sentence,
never invented facts), but have a human editor spend focused time only
on the top 20% of SKUs that drive roughly 80% of revenue, checking those
specifically for the E-E-A-T signals (genuine expertise, evidence,
sourcing) that both search engines and generative engines weight most
heavily on the highest-stakes pages.

## Watch-outs

- **Optimizing only the head-query page and ignoring the fan-out.** The
  measured 7-12% overlap between traditional top-10 rankings and AI
  citations is the concrete evidence that head-query-only optimization
  systematically misses generative-engine visibility — the sub-question
  pages are not optional extras, they're where most of the citation
  opportunity actually lives.
- **Using unverifiable superlatives instead of specific claims.** "The
  best," "revolutionary," "exceptional" are exactly the phrasing pattern
  generative engines are documented to discount — a specific number, a
  named comparison, or a sourced test result is what gets extracted and
  cited instead.
- **Auto-publishing AI-generated bulk copy with zero human review on a
  full catalog.** The specific documented risk is "SEO sludge" —
  content grounded in nothing verifiable, which both degrades citation
  odds (vague claims don't extract cleanly) and creates an accuracy/E-E-A-T
  liability on the highest-traffic SKUs specifically.
- **Treating the "GEO cluster" (buying guide, comparison, long-term
  review) as optional content marketing rather than part of the core
  GEO strategy.** In the documented case, the supporting-content traffic
  grew 600% and these pages were a direct source of new citations — the
  product page alone did not carry the full result.
- **Naming competitors dishonestly or inflating comparison claims.** The
  documented case's comparison content explicitly conceded where the
  product lost (long-distance cushioning, brand recognition) alongside
  where it won (value, wet-rock grip) — a generative engine synthesizing
  from confidently-worded but inaccurate content is a documented failure
  mode from the model's side (`../seo/generative-engine-optimization.md`'s
  own watch-outs section), not a strategy to lean into from the
  publisher's side.

## Related

- **`../seo/generative-engine-optimization.md`** — the general GEO
  discipline and diagnostic baseline (asking target AI assistants the
  real questions) this note's product-copywriting application builds on
  directly; read that note first if the general mechanism isn't already
  familiar.
- **[product-feed-schema-optimization.md](product-feed-schema-optimization.md)**
  — the structured-data layer (schema.org `Product`/`Offer`/
  `AggregateRating`, the 40-60 word citable-passage rule at the field
  level) this note's prose guidance sits directly on top of.
- **[dropshipping-supplier-platforms.md](dropshipping-supplier-platforms.md)**
  — the fulfillment/sourcing decision that has to be settled before this
  note's copywriting work is worth investing in at scale; a product with
  an unresolved fulfillment-speed or return-rate problem
  (`platform-ranking-algorithms.md`) won't convert on citation traffic
  even once it's earning it.
