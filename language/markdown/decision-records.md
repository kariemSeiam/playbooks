# Decision records — a durable "why," per hard-to-reverse choice

[document-types.md](document-types.md) already classifies an agent's `MEMORY.md` as
append-only explanation — a log of why past decisions were made. An ADR
(Architecture Decision Record) is the same idea at project-repo scope
instead of session scope: one file per genuinely hard-to-reverse choice,
numbered, cross-referenced, checked into the repo itself rather than a
private memory system, so the reasoning survives regardless of which
assistant session or which human touches the project next.

This pattern shows up unformalized in real projects — a `spec/` folder
with its own `archive/adr/README.md` embedding exactly this template
inline is a common ad hoc version. This file generalizes it so any
project can adopt it without re-deriving the format from scratch.

## When to write one

- Switching a framework, transport, or a public API's shape
- Dropping support for something (a runtime version, an integration)
- Any choice a new contributor would reasonably ask "wait, why not X
  instead?" about, where the answer isn't obvious from reading the code

## When not to

- A decision that's easily reversed (a variable name, a file's location,
  which linter config to start from) — an ADR for a cheap-to-undo choice
  is ceremony without payoff, exactly what this vault's own feedback
  memory (`no-ceremony-for-ephemeral-artifacts`) already warns against.
- A decision that's already fully explained by the code and a commit
  message — don't create a duplicate record of the same fact
  ([preflight-checklist.md](preflight-checklist.md)'s cross-reference rule).

## The template

```markdown
# ADR-NNN: Title

## Status
Proposed | Accepted | Superseded by ADR-XXX

## Context
What forces this decision? What were the actual alternatives considered,
not just the one chosen?

## Decision
What we're doing, stated plainly, one paragraph.

## Consequences
What this makes easier, what it makes harder, what follow-up work it
creates. Include the negative consequences — an ADR that only lists
upsides isn't a real decision record, it's a justification.
```

## Numbering and supersession

Number sequentially (`ADR-001`, `ADR-002`, ...), never reuse a number,
and never edit a decided ADR's `Decision` section after the fact — if the
decision changes, write a new ADR with `Status: Accepted` and set the old
one's status to `Superseded by ADR-XXX`. The record of "we used to think
X, then learned Y, so we do Z now" is itself valuable; overwriting the old
file erases exactly the information a future reader most needs when
they're about to ask "why didn't we do X."

## Where these live

One `adr/` (or `docs/adr/`) folder per repo, with its own [README.md](README.md)
index listing every ADR by number and current status — the same
"index + individual files" shape this playbook itself uses
([README.md](README.md)'s own file listing). A project with fewer than two or three
hard-to-reverse decisions doesn't need the folder yet; create it when the
first one is actually written, not preemptively.
