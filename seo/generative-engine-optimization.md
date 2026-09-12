---
domain: seo
concept: Generative Engine Optimization (GEO/AEO) — getting cited by LLM-synthesized answers
source: research — synthesized from 2026 GEO/AEO practitioner guidance (query fan-out, authority-signal citation tactics, llms.txt/AI-crawler adoption), 2026
tags: [seo, geo, aeo, llm, ai-search, llms-txt, citations]
---

# Generative Engine Optimization (GEO/AEO)

GEO — also called AEO (Answer Engine Optimization), AI SEO, or AIO,
all names for the same practice — is optimizing content so an LLM
(ChatGPT, Claude, Gemini) cites it as a trusted source inside a
synthesized answer, rather than optimizing to rank as a clicked blue
link. A consultant needs this as a genuinely distinct discipline, not
"SEO with an AI label," because the underlying retrieval mechanism is
different in a way that changes what "optimized" means: a traditional
search engine returns a ranked list for a human to parse and choose
from; a generative engine breaks the question into sub-queries, retrieves
across many of them, and synthesizes one answer — visibility means being
one of the sources woven into that synthesis, not the top blue link.

## When to use

- A client's category is starting to see real query volume shift from
  traditional search to AI assistants (ChatGPT, Perplexity, AI Overviews,
  Claude) for comparison and "best of" questions — the traffic isn't
  disappearing, it's arriving as a citation or not arriving at all.
- Evaluating why a client with strong traditional SEO rankings isn't
  showing up when the same questions are asked of an AI assistant — the
  two are measuring different things and require different diagnostics.
- Building or auditing any content meant to be a reference/authority
  source (documentation, comparison guides, "best X for Y" content) —
  this is exactly the content type generative engines lean on most.
- A technical audience client (a developer tool, an API, an open-source
  project) whose actual buyers are increasingly asking an AI assistant
  "what's the best tool for X" instead of searching directly — this
  vault's own `extensions/` and `seo/` content is itself in this category.

## How it works

**Query fan-out.** A generative engine doesn't run the user's literal
question against an index the way a search engine does — it decomposes
the question into several sub-queries and retrieves separately for each,
then synthesizes across the results. "What's the best VPN for streaming
Netflix in Europe" becomes something closer to three separate retrievals:
"best VPN 2026," "VPN Netflix streaming," "VPN Europe servers." Content
that only answers the exact top-level question, and not the sub-questions
underneath it, is invisible to most of the fan-out even if it would have
ranked well for the literal query in traditional search.

**The tactics with the strongest evidence, most effect first:**

1. **Build on solid traditional SEO first** — GEO doesn't replace the
   three pillars (`fundamentals.md`); it adds a layer on top. Content a
   crawler can't reach or parse is invisible to both search and
   generative engines equally.
2. **Cite authoritative sources and quote named experts** — synthesized
   answers favor content that itself demonstrates sourcing discipline,
   not unsupported assertion.
3. **Add specific statistics and write in confident, declarative
   prose** — vague hedged language is harder for a retrieval system to
   extract a clean, citable claim from than a specific, stated number or
   fact.
4. **Cover the query fan-out, not just the headline query** — answer the
   two or three sub-questions a real question decomposes into, not only
   the literal phrasing.
5. **Own comparison and "best-of" queries in the category** — this is
   disproportionately where generative engines lean on external content,
   because synthesizing a genuine comparison from scratch is exactly the
   kind of task an LLM benefits from an existing authoritative source for.
6. **Seed the sources the engines themselves trust** — being cited on a
   handful of sites the model's own training/retrieval already weights
   heavily is worth more than volume across low-authority ones.
7. **Keep content fresh** — recency is a stronger signal for AI
   synthesis than for traditional ranking, since a generative engine is
   more likely to be answering a time-sensitive "what's current" framing.

**The technical layer.** Explicitly allow the AI crawlers a client wants
indexed (`robots.txt` entries for the specific bot user-agents, not just
the generic rule), ship JSON-LD schema so an entity's structured facts
are machine-extractable rather than requiring the model to infer them
from prose, and publish an `llms.txt` (`../language/markdown/llms-txt.md`)
— a machine-readable index specifically for AI crawlers, the GEO
equivalent of an XML sitemap for a traditional search engine.

## Example

An open-source developer tool has strong GitHub stars and solid
traditional SEO on its documentation site, but when someone asks an AI
assistant "what's a good MCP server for geocoding," a competitor gets
cited instead — despite the client's tool being technically better.
Diagnosis: the competitor's README explicitly answers the comparison
question ("Instead of X, you get Y" — the fan-out sub-query "MCP
geocoding comparison" resolves to their page), states specific benchmark
numbers instead of vague "fast and reliable" language, and ships an
`llms.txt`. The client's docs are accurate but hedge every claim
("may improve performance in some cases") and never directly address the
comparison framing a real buyer's question fans out into.

## Applying it for a client

Start by testing the actual gap, not assuming one exists: ask the target
AI assistants the client's real target questions and record whether the
client is cited, a competitor is cited, or neither. This is the GEO
equivalent of a rank-tracking baseline and it's cheap to run manually
before recommending any work. When a gap is real, prioritize the
comparison/best-of content type and the technical layer (llms.txt,
crawler permissions, schema) before broad content expansion — those are
the items with the most effect for the least work, per the ranking above,
and they're checkable in a way vague "write more authoritative content"
advice isn't.

## Watch-outs

- **Treating GEO as a replacement for traditional SEO rather than a
  layer on top of it.** The tactics with real evidence behind them start
  with "build on solid SEO" — a client abandoning traditional SEO
  investment for GEO-only tactics is optimizing for a channel that still
  depends on the foundation they just cut.
- **Gaming citation-bait content without underlying substance.**
  Generative engines synthesizing from confidently-worded but inaccurate
  content is a real, documented failure mode from the model's side, not
  a strategy to lean into from the publisher's side — content that gets
  cited once and is later found wrong or manipulative is a reputational
  risk, not a repeatable channel.
- **No stable baseline.** Unlike traditional rank tracking, there's no
  universally standardized way yet to measure "citation share" across
  assistants — a client asking to prove GEO ROI numerically needs an
  honest conversation about measurement immaturity in this specific
  channel, not a fabricated dashboard.
- **Ignoring that different assistants retrieve differently.** A tactic
  that improves citation in one AI assistant doesn't automatically
  transfer to another — treat each as its own channel worth testing
  separately, the same discipline already applied to separate search
  engines.

## Related

- **[fundamentals.md](fundamentals.md)** — the traditional SEO layer this discipline
  builds on rather than replaces.
- **`../language/markdown/llms-txt.md`** — the concrete technical
  mechanism (the `llms.txt` spec) this note's technical-layer section
  points to.
- **[developer-platform-discoverability.md](developer-platform-discoverability.md)** — GEO applied specifically to a
  GitHub/open-source presence, where "best MCP server for X"-style
  comparison queries are exactly the fan-out this note describes.
