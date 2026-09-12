---
domain: software-engineering
concept: AI agent architecture patterns — ReAct, tool use, planning, reflection, multi-agent, RAG, human-in-the-loop
source: research — synthesized from 2026 production AI agent architecture references (Redis engineering blog, industry pattern surveys on ReAct/tool-use/multi-agent orchestration), 2026
tags: [ai-agents, llm, orchestration, rag, agent-design, tool-use]
---

# AI agent architecture patterns

Seven patterns separate an agent that works reliably in production from
one that only worked in a demo, and they combine rather than compete:
planning decomposes a task, ReAct executes each step, tool use handles
real-world interaction, RAG supplies knowledge the model doesn't have,
reflection checks the work, human-in-the-loop gates the consequential
parts, and multi-agent orchestration offloads specialization when one
agent's context or focus would otherwise overload. Most production
failures trace to skipping one of these where the task actually needed
it, not to picking the wrong pattern outright.

## When to use

- **ReAct** — almost universally; it's the foundational reason-then-act
  loop underneath most working agents, not a special-case pattern.
- **Tool use** — any agent that needs to affect or read something outside
  its own context window (a file, an API, a database).
- **Planning** — tasks requiring five or more sequential, interdependent
  steps, where losing track of the original goal partway through is a
  real risk.
- **Reflection** — tasks with a checkable quality bar (code that must
  compile, structured data that must validate, writing that must meet a
  stated standard) — not tasks with no clear "better" to revise toward.
- **Multi-agent orchestration** — a task genuinely decomposes into
  independent specializations, or needs parallel work a single agent's
  context can't hold at once — not merely because a task "feels big."
- **RAG** — knowledge-intensive tasks where the needed information isn't
  in the model's training data or the current context, and exists in a
  retrievable corpus.
- **Human-in-the-loop** — any agent taking a consequential, hard-to-
  reverse real-world action (deleting data, sending external
  communication, spending money).

## How it works

**ReAct (Reason + Act)** — the agent alternates a reasoning step and an
action step in a closed loop, each action's observation feeding the next
reasoning step. This is the loop most agent frameworks build on top of;
its cost is token overhead per reasoning step, which matters for
high-frequency, low-complexity tasks (simple classification) more than
for genuinely complex ones.

**Tool use / function calling** — the model selects from a defined tool
set, generates structured parameters, and receives results back into
context; the model itself never executes anything directly. The contract
between model and tool is exactly the API contract problem
([rest-api-design.md](rest-api-design.md)): the tool's schema is a stable interface the
model depends on, and the tool's actual implementation can change freely
behind it.

**Planning (plan-and-execute)** — the agent produces an explicit
multi-step plan before acting, then executes and revises step by step.
Storing the plan as structured, queryable data (not prose buried in a
transcript) is what makes it possible to check progress against the
original goal and debug where a long task went wrong.

**Reflection** — after producing output, the agent evaluates its own work
against stated criteria, and revises if it doesn't meet them. This only
works with a concrete, checkable standard — "make this better" produces
unfocused revision; "does this pass the type checker" or "does this match
the five required fields" produces convergent revision.

**Multi-agent orchestration** — two shapes: a supervisor pattern (one
orchestrator delegates to specialists and integrates their results) or a
peer pattern (agents negotiate without central coordination). The
supervisor pattern is the more common production shape because it has a
clear termination condition (the orchestrator decides when the task is
done); the peer pattern risks circular back-and-forth with no natural
stopping point.

**RAG-augmented agents** — distinct from a static RAG pipeline: the agent
itself decides when to retrieve, what to search for, and how to combine
multiple retrieved pieces, rather than retrieval happening once
automatically before generation. Precision matters more than raw
retrieval — a single similarity search often surfaces related-but-wrong
context; production systems add query decomposition and re-ranking on
top of raw vector similarity.

**Human-in-the-loop** — the agent has an explicit mechanism (typically a
confidence threshold, or a hard rule for specific action types) to pause
and escalate rather than act. The escalation itself needs to carry enough
context for a human to actually resolve it quickly — an escalation with
no context just moves the bottleneck from the agent to an overwhelmed
human.

## Example

A production coding agent handling "implement this feature and open a
PR": **planning** breaks the task into ordered steps (read the relevant
files, design the change, implement, test, open the PR); **ReAct** drives
execution of each step, observing tool results and adjusting; **tool
use** is how it reads files, runs the test suite, and calls the git/GitHub
API; **RAG** pulls in relevant internal documentation or prior similar
changes if the codebase has a searchable corpus; **reflection** re-checks
the diff against the stated requirement and the test suite's output
before considering the step done; **human-in-the-loop** gates the actual
PR creation and, separately, anything that would touch production
infrastructure directly; **multi-agent orchestration** enters only if the
task genuinely splits (e.g., a frontend-specialist agent and a
backend-specialist agent working in parallel on independent parts of one
feature) — for a single-file bug fix, adding a second agent would be
coordination overhead with nothing to coordinate.

## Applying it for a client

Diagnose which pattern is actually missing before recommending a bigger
architecture change — most "the agent is unreliable" complaints trace to
one specific gap: no reflection step (so bad output ships unchecked), no
structured plan storage (so long tasks drift off the original goal), or
tool calls with no retry/validation (so a transient failure looks like
the agent "hallucinating" a wrong action). Multi-agent orchestration is
the pattern most often reached for prematurely — recommend it only once a
client can name the specific, independent specializations that justify
it, since every additional agent multiplies the debugging surface, and a
single well-scoped agent with good tool use and reflection often
outperforms an under-designed multi-agent system. For any client building
agents that touch real money, real customer communication, or
irreversible data operations, human-in-the-loop gating on those specific
action types is the one pattern to insist on regardless of budget or
timeline pressure — it's the cheapest insurance against the most
expensive category of failure.

## Watch-outs

- ReAct without structured logging of each reasoning step makes
  debugging a failure nearly impossible after the fact — the transcript
  exists, but without structure, finding *which* step went wrong means
  re-reading the whole thing.
- Reflection needs an iteration limit; without one, an agent unsatisfied
  with its own output can loop indefinitely, especially with vague
  self-set criteria.
- Multi-agent orchestration's coordination overhead is a real cost, not a
  neutral architectural choice — it needs to be justified by genuine task
  decomposition, not used as a default "more agents = more powerful"
  reflex.
- RAG without a re-ranking step after vector similarity search will
  surface plausible-but-wrong context often enough to matter; treat raw
  similarity search as a first pass, not the final retrieval step, for
  anything where precision matters.
- Human-in-the-loop escalation paths designed after an agent is already
  deployed tend to give humans too little context to resolve issues
  quickly — design the escalation payload (what a human needs to see to
  decide) at the same time as the trigger condition, not afterward.

## Related

- [rest-api-design.md](rest-api-design.md) — a tool's schema in an agent architecture is the
  same stable-contract problem as an API endpoint; the same discipline
  (versioning, clear errors) applies when a tool's interface needs to
  change.
- [software-architecture-principles.md](software-architecture-principles.md) — multi-agent orchestration is
  coupling/cohesion applied to agents: each specialist needs a narrow,
  stable contract with the orchestrator for exactly the reason a
  well-designed service needs one with its callers.
