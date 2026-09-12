# Writing markdown for an agent's own future consumption

This is the one genuinely non-obvious finding, worth its own file: a
markdown document written for an AI agent to read — including this one,
including any agent's own memory files — has different needs than one
written purely for a human, and the difference isn't stylistic, it's
structural.
The core idea, from the progressive-disclosure / "book pattern" research:
**markdown for an agent should be indexable first, readable second** —
the reverse priority of classic prose, where being pleasant to read
straight through is the main goal.

## Why this is a real distinction, not a nuance

A human opens a document once and reads it in whatever order the author
chose. An agent doesn't read a document — it *decides whether to load it
at all*, then, if so, scans structure before committing to reading
content, because every token loaded is a real cost paid against a real
budget. A document optimized for the human case (a smooth narrative,
context built up before the point) is actively worse for the agent case,
because the agent needs the decision-relevant structure — what is this,
is it relevant, how much would it cost to load — before it's willing to
pay for the content at all.

## The three-tier structure (cover / chapter / appendix)

This vault already implements this pattern in its actual mechanics, not
just in theory — naming it explicitly makes it something to design *for*
on purpose rather than something that happened to fall out of tool
design:

- **Tier 1 (cover)** — name + one-line description, always loaded, cheap.
  This is exactly what a Skill's frontmatter is, what a deferred tool's
  name is before `ToolSearch` fetches its schema, what `CONTEXT.md`'s one
  pointer-line to a playbook is. The reader (agent) decides relevance from
  this alone, at near-zero cost.
- **Tier 2 (chapter)** — full content, loaded only when tier 1 signaled
  relevance. A playbook topic file, a fetched tool schema, a skill's full
  body. Priced in the low thousands of tokens, not free, but only paid
  when tier 1 already justified it.
- **Tier 3 (appendix)** — long examples, detailed scripts, exhaustive
  reference — loaded only when explicitly asked for by name from within a
  tier-2 document. Unbounded size, because it's never loaded speculatively.

**The rule that makes this actually work**: an appendix that isn't
referenced by name from some chapter is invisible — nothing will ever
decide to load it, because nothing pointed at it. Every tier-3 file needs
a tier-1 or tier-2 pointer, or it doesn't effectively exist.

## Concrete rules that follow from this

- **Front-load the answer in every file, every section — no exceptions.**
  An agent that loads a document and reads only the first paragraph
  before deciding whether to keep going should already have the
  substance, not a promise that the substance is coming.
- **Put decision-relevant metadata in a structured form (a table), not
  buried in prose.** A budget number, a size limit, a confidence score, a
  status — these are things an agent parses to decide what to do next;
  prose forces it to extract structured facts from unstructured text,
  which is strictly harder and less reliable than reading a table cell.
- **State size/token budgets explicitly on anything meant to be loaded
  routinely** (this vault already does this — `CONTEXT.md` ≤80 lines,
  `MEMORY.md` ≤150 lines) and, critically, **say what happens when the
  budget is hit**, not just the number — a budget with no overflow rule
  just gets silently exceeded the first time it matters.
- **Prefer a short, consistently-used tag/symbol over a full descriptive
  phrase for a category that recurs often** (this vault's own `NERVE`
  sigils — `~` task, `^` decision, `?` question, `!` blocker, `*` pattern,
  `>` log, `=` state — are exactly this pattern already). A single
  consistent symbol is both cheaper to emit and, once learned, faster to
  recognize than re-reading a full word every time.
- **Use hierarchy to let a reader (agent or human) stop early and still
  have gotten something.** A file that reads correctly if you stop after
  its first heading, more correctly if you read the first two, and fully
  correctly only at the end, degrades gracefully under a token budget
  instead of failing outright the moment the budget runs out mid-document.

## Where this changes what "good markdown" means, compared to [voice.md](voice.md)

[voice.md](voice.md)'s scannable-first principle already points the same direction
for human readers — that's not a coincidence, it's the actual thesis of
this whole playbook (see [README.md](README.md)): the discipline that makes a
document good for a human to scan and the discipline that makes it good
for an agent to navigate are the same discipline, not two different ones
in tension. This file exists to make explicit the one place they diverge
further than "same idea, different word for it": an agent's real,
metered, per-token cost of loading content at all is a constraint a human
reader never faces the same way — which is why tiering (cover/chapter/
appendix) and structured metadata (tables, budgets, tags) earn their
place here specifically, even in documents no human will ever read start
to finish.
