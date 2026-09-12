---
domain: people-org
concept: Decision Rights Frameworks — RACI, RAPID, DACI
source: research — DuPont-era responsibility charting; Bain & Company, "Who Has the D?" (HBR, 2006); Atlassian playbook
tags: [decisions, accountability, roles, clarity, governance]
---

# Decision Rights Frameworks — RACI, RAPID, DACI

These three frameworks solve the same underlying failure — work stalling because nobody is sure who has to act, who has to say yes, and who just needs to know — but they solve it at different altitudes. RACI is a task-clarity tool: it maps roles onto a project's activities. RAPID and DACI are decision-clarity tools: they map roles onto a single decision, which matters more as an organization grows, because most organizational drag doesn't come from unclear tasks, it comes from decisions that get re-litigated three times because nobody agreed in advance who actually holds the "D." All three are battle-tested — RACI traces to mid-20th-century responsibility-charting practice in large industrial and government projects, RAPID was formalized by Bain & Company (Paul Rogers and Marcia Blenko, in the 2006 Harvard Business Review article "Who Has the D?"), and DACI is Atlassian's widely-adopted internal variant, popularized through its public team-playbook.

## When to use

- A project has clear deliverables but work keeps stalling because people don't know if they're supposed to act, approve, or just watch — use **RACI**.
- A specific decision (a pricing change, a vendor choice, a re-org) is looping between stakeholders with no one willing to call it — use **RAPID** or **DACI**.
- Cross-functional friction where "consulted" and "responsible" have quietly become interchangeable, and someone who should only give input is effectively vetoing.
- Onboarding a new leader or restructuring a team, when it's the moment to explicitly re-draw who owns what before old, unspoken assumptions calcify again.
- A governance review for a client whose meetings keep re-deciding things that were "already decided" last month — almost always a sign no one was ever actually assigned the D.

## How it works

### RACI — for tasks and activities

| Letter | Role | Rule |
|---|---|---|
| **R**esponsible | Does the work | Can be multiple people |
| **A**ccountable | Owns the outcome, signs off | Exactly one person per task — this is RACI's most-broken rule |
| **C**onsulted | Two-way input sought *before* the work is done | Their input shapes the outcome; they don't have veto power |
| **I**nformed | Told *after* the decision or work is complete | One-way communication, no input expected |

RACI is built as a matrix: tasks/activities down the rows, roles across the columns, one letter per cell. Its unit of analysis is the *task*, which is why it works well inside a single project plan but gets awkward applied to a single ambiguous decision — RACI doesn't have a native concept of "who breaks the tie."

### RAPID — for decisions, Bain's model

| Letter | Role | What they do |
|---|---|---|
| **R**ecommend | Proposes the course of action, gathers the analysis and other inputs | Owns building the case |
| **A**gree | Must sign off before it proceeds — holds a genuine veto | Used sparingly; too many Agrees re-creates committee paralysis |
| **P**erform | Executes once the decision is made | Often overlaps with Recommend |
| **I**nput | Provides data, expertise, or perspective | No veto — this is RAPID's answer to RACI's "Consulted," made explicitly non-blocking |
| **D**ecide | The single person who makes the call and is accountable for it | Exactly one — Bain's central finding is that decisions with a clear, single D get made faster and better than decisions run by consensus |

Bain's research (surveying thousands of managers) found that decision quality, speed, and effort correlate most strongly with **role clarity on a single decision**, not with org structure or headcount — companies that could name who held the D on their major decisions consistently out-executed those that couldn't.

### DACI — Atlassian's variant

| Letter | Role | Note |
|---|---|---|
| **D**river | Runs the process — schedules, gathers input, drives toward a decision | Often not the decision-maker themselves; this is the person who makes sure it doesn't stall |
| **A**pprover | Makes the final call | Usually one person, occasionally a small named group with a stated tie-break |
| **C**ontributor | Gives input | Analogous to RAPID's Input / RACI's Consulted |
| **I**nformed | Told the outcome | Analogous to both other frameworks |

DACI's distinguishing feature versus RAPID is separating "who drives the process" (Driver) from "who decides" (Approver) — useful when a program manager needs to own getting a decision made without themselves having the authority to make it.

### Choosing between them

| Situation | Best fit |
|---|---|
| A multi-step project with many discrete deliverables | RACI |
| One high-stakes, cross-functional decision (pricing, M&A, platform choice) | RAPID |
| A decision that needs a named process-owner distinct from the decision-owner | DACI |
| Small team, low ambiguity | Often none needed — imposing a framework where trust already exists adds ceremony without benefit |

## Example

A retail client is choosing a new POS vendor — three finalists, four stakeholders (CFO, Head of Retail Ops, IT Director, CEO) stuck in a fourth meeting re-arguing the same trade-offs.

Applying RAPID:

- **Recommend:** Head of Retail Ops — builds the comparison, runs vendor demos, drafts the recommendation.
- **Input:** IT Director (integration risk), Store Managers (usability feedback), Finance analyst (total cost of ownership).
- **Agree:** CFO — must sign off because the contract commits multi-year spend; holds real veto on cost terms only.
- **Decide:** CEO — makes the final call, informed by the Recommend and the CFO's Agree.
- **Perform:** IT Director's team — executes the migration once decided.

The fourth meeting stops happening because "who decides" is no longer ambiguous — Retail Ops brings a recommendation, Finance either agrees or names the specific blocking term, and the CEO decides. Compare this to a RACI chart for the same project, which would map dozens of implementation tasks (contract review, data migration, staff training) but wouldn't, by itself, resolve who breaks the vendor-choice deadlock — that's exactly the gap RAPID/DACI are built to close.

## Applying it for a client

Diagnose before prescribing: if the client's complaint is "nobody knows what they're supposed to be doing on this project," draw a RACI matrix over their actual project plan. If the complaint is "we keep re-deciding the same thing," that's a decision-rights problem, not a task-clarity problem — reach for RAPID or DACI instead, and resist the urge to force-fit RACI onto a single decision (it will produce an Accountable owner but no mechanism for the veto-vs-input distinction that actually unsticks decisions). Whichever framework you use, do the exercise live with the actual stakeholders in the room — a decision-rights chart built solo and emailed out gets silently ignored the first time it's inconvenient, because it was never actually agreed to, just announced. Keep the Agree/Approver list short (1-2 people); the framework's value comes specifically from forcing an org to *not* require broad consensus, and a long Agree list quietly re-creates the committee-paralysis these tools exist to kill.

## Watch-outs

- The single most common failure across all three: naming more than one Accountable/Decide/Approver "to be safe." This isn't caution, it's the exact ambiguity the framework was supposed to remove — one name only.
- Confusing Consulted/Input/Contributor with veto power. If a stakeholder can block the outcome, they are Agree/Approver, not Input — mislabeling this is how "lightweight input" quietly becomes an informal veto that nobody agreed to.
- Drawing the chart once and never revisiting it. Roles that made sense at project kickoff (e.g., who's Accountable) often need to shift as a project moves from design into execution — a stale RACI is worse than none, because people trust a document that's no longer true.
- Using RACI for a decision when what's needed is RAPID/DACI (see How it works) — the wrong altitude of tool leaves the actual pain point (repeated re-litigation) untouched even after the matrix is filled in.
- Treating the framework as the fix rather than the forcing function — the chart doesn't resolve disagreement about *what* the right call is, only about *who* gets to make it. Deploy it after real alignment work (see [five-dysfunctions-of-a-team.md](five-dysfunctions-of-a-team.md) on conflict and commitment), not as a substitute for it.

## Related

- [okrs-execution.md](okrs-execution.md) — an OKR names *what* needs to happen this quarter; RACI/RAPID/DACI names *who* decides and executes it.
- [five-dysfunctions-of-a-team.md](five-dysfunctions-of-a-team.md) — decision-rights clarity only works on a team that can already have honest conflict and commit to a call once made; without that foundation, naming a Decide/Approver just moves the argument, it doesn't end it.
- [org-design-star-model.md](org-design-star-model.md) — the Structure point of the Star Model determines where formal authority sits; RAPID/DACI operationalize that authority for a specific decision.
