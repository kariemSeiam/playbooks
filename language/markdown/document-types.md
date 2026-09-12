# Document types — know which one you're writing

Diátaxis's core finding, distilled: there are four distinct things a
document can be, they serve genuinely different needs, and a document
that tries to be more than one of them at once ends up serving none of
them well. Before writing anything non-trivial, know which one this is.

## The four kinds

|  | **Action** (what to do) | **Cognition** (what to know) |
|---|---|---|
| **Study** (acquiring understanding) | **Tutorial** — a guided first experience, learning by doing | **Explanation** — context, reasoning, the "why" behind something |
| **Work** (applying understanding) | **How-to guide** — steps toward a specific real goal, for someone already competent | **Reference** — neutral facts, used while working, not read start-to-end |

- **Tutorial**: "teach me by doing." Written for someone who doesn't yet
  know this and needs a safe, guided first success. Not the place for
  every option or edge case — that's what reference is for.
- **How-to guide**: "help me accomplish X." Written for someone who
  already knows the basics and has a specific real task in front of them.
  Doesn't need to teach fundamentals, doesn't need to explain why — it
  needs to work, in order, right now.
- **Reference**: "tell me the facts." Neutral, complete, organized to
  match the actual structure of the thing it describes (not the order
  someone would learn it in). Consulted mid-task, not read cover to
  cover — a reader dips in for one fact and leaves.
- **Explanation**: "help me understand why." Not needed to get the
  immediate task done — read when the reader wants to actually understand
  the reasoning, the trade-off, the history behind a decision.

## The mistake worth naming: mixing modes in one document

A how-to guide that stops to explain background theory loses the reader
who just wanted the steps. A reference page that editorializes about
which option is best stops being neutral and becomes unreliable as a
lookup. A tutorial that tries to cover every edge case stops being a safe
guided first experience and becomes overwhelming. The fix is never "write
a better hybrid" — it's separate documents, each honest about which of
the four jobs it's doing, cross-linked where one naturally leads to
another.

## Where an AI agent's own memory files land

- **`CONTEXT.md`** — **reference.** Facts about a project as it stands
  right now, organized by the project's actual shape, not a narrative.
  Consulted, not read start to finish.
- **`MEMORY.md`** — **explanation, in append-only log form.** Each entry
  is a small explanation of why a past decision was made — the "why," not
  a how-to for redoing it.
- **`ACTIVE.md`** — **reference**, specifically of the "where things
  stand right now" kind — closer to a status snapshot than either
  narrative type.
- **A playbook's checklist file** (e.g. [preflight-checklist.md](preflight-checklist.md)) — **how-
  to guide.** Steps, in order, for someone already competent, about to do
  a specific real thing right now. Not the place to re-argue why each
  step matters — that's the other files' job.
- **A playbook's topic files** (e.g. this playbook's own [syntax.md](syntax.md) and
  [voice.md](voice.md), or `playbooks/github/commits.md`) — **reference blended
  with explanation**: facts stated as law, each with
  the reasoning attached, meant to be dipped into for one answer, not
  read straight through. This is legitimate — Diátaxis's objection is to
  mixing modes within one document, not to a folder containing several
  documents of different types that reference each other. The playbook
  structure already does this correctly by having a separate checklist
  file instead of interleaving "do this" steps into the reference prose.

## The practical rule

Before writing a new file (or a new section in an existing one), name
which of the four it is in one word. If the honest answer is "more than
one," it's not one document yet — split it, the way the checklist file is
already split from the reference files in this same playbook.
