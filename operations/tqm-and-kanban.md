---
domain: operations
concept: TQM and Kanban
source: 'research — W. Edwards Deming, Out of the Crisis (1986); David J. Anderson, Kanban: Successful Evolutionary Change for Your Technology Business (2010)'
tags: [quality, kanban, continuous-improvement, workflow, wip]
---

# TQM and Kanban

Total Quality Management (TQM) is a management philosophy that makes quality everyone's ongoing responsibility across the whole organization, not a single department's inspection job — it was built up through the work of W. Edwards Deming, Joseph Juran, and Philip Crosby, largely proven out in Japanese manufacturing after WWII, and later formalized for Western management in works like Deming's *Out of the Crisis* (1986). Kanban is a visual, pull-based method for managing workflow with strict limits on how much work is in progress at once — it originated as a physical card system Taiichi Ohno built at Toyota to control just-in-time inventory replenishment on the shop floor, and was later adapted for knowledge work and IT by David J. Anderson in *Kanban: Successful Evolutionary Change for Your Technology Business* (2010). A consultant needs both together because TQM sets the *cultural* target (everyone owns quality, continuously) while Kanban provides one of the most practical *mechanical* tools for actually managing the flow of work toward that target without overloading the team producing it.

## When to use

- A client treats quality as a final inspection step rather than something built into every stage of work — TQM reframes where quality actually needs to live.
- A team's work is invisible — nobody can see, at a glance, what's in progress, what's stuck, or how much everyone is actually carrying at once — Kanban's visual board solves this directly.
- A client wants process improvement but can't tolerate a disruptive, all-at-once methodology change — Kanban's evolutionary approach ("start with what you do now") fits teams that need change to be gradual.
- Diagnosing chronic overload: staff juggling too many simultaneous tasks, with everything half-finished and nothing actually shipping — a classic missing-WIP-limit symptom.
- Introducing a quality culture to a client whose only current quality mechanism is a founder personally checking everything before it goes out.

## How it works

### TQM's core commitments

TQM is less a fixed toolkit than a set of organizational commitments, most influentially shaped by Deming's teaching in Japan and later distilled into "14 points" for management. The commitments that matter most for a consultant to recognize in a client organization:

- **Quality is built in, not inspected in** — defects should be prevented at the source, not caught and discarded at the end of the line; an end-of-line inspection step is a symptom that quality isn't yet built into the process itself.
- **Continuous improvement (kaizen) as an ongoing habit**, not a one-time initiative — this is the same discipline Lean Six Sigma's Control phase locks in, applied as an organization-wide culture rather than a single project's closing step.
- **Everyone owns quality** — from frontline staff to senior management, not a single quality-control department acting as the sole gatekeeper.
- **The Deming (PDCA) cycle** — Plan-Do-Check-Act as the basic unit of improvement, run repeatedly rather than once; this same cycle later became the operating structure of ISO 9001.
- **Reduce fear, remove barriers between departments** — two of Deming's more pointed 14 points, aimed directly at the organizational dynamics (blame, siloed departments) that suppress the honest reporting of quality problems.

TQM's direct legacy shows up in two frameworks already documented elsewhere: ISO 9001 formalizes TQM's principles into an auditable standard, and Six Sigma's statistical rigor descends from the same quality movement, applied with tighter measurement discipline.

### Kanban's origin and core practices

Kanban ("signboard" or "visual card" in Japanese) began as a literal card attached to a bin of parts at Toyota — when the bin emptied, the card was the signal to replenish it, which is what kept production pulling material only as fast as it was actually being consumed, rather than pushing material ahead of demand. Anderson's adaptation for knowledge work keeps the same pull logic but replaces physical bins with a visual board of work items. Six core practices define it:

| Practice | What it means |
|---|---|
| **Visualize the workflow** | Make every unit of work and every stage it passes through visible on a shared board, usually columns like To Do / In Progress / Review / Done. |
| **Limit work in progress (WIP)** | Cap the number of items allowed in each column at once — this is the single practice that distinguishes Kanban from "a to-do list with columns," and it's the mechanism that actually improves flow. |
| **Manage flow** | Watch how work items move through the board, and actively address where they stall, rather than just watching individual people's busyness. |
| **Make policies explicit** | Write down, visibly, what "done" and "ready to pull" mean for each column, so the rules aren't tribal knowledge. |
| **Implement feedback loops** | Regular, cadence-based reviews of the board and the flow metrics below, so the system corrects itself. |
| **Improve collaboratively, evolve experimentally** | Change the process through small, agreed experiments rather than a wholesale redesign — the "evolutionary" half of the method's own name. |

### Flow metrics

| Metric | What it measures |
|---|---|
| **Lead time** | Total elapsed time from when a work item is requested to when it's delivered. |
| **Cycle time** | Elapsed time from when work actually starts on an item to when it's done — a subset of lead time. |
| **Throughput** | How many items complete per unit of time. |
| **Cumulative flow diagram** | A stacked area chart of items in each workflow stage over time — a widening band in any one stage is a direct visual signal of a bottleneck forming there. |

### Why Kanban fits change-averse teams

Unlike frameworks that require an organization to adopt new roles and ceremonies on day one, Kanban's starting instruction is explicitly "start with what you do now" — visualize the existing process first, add WIP limits second, and let subsequent changes emerge from what the board and metrics reveal, rather than mandating a new process structure up front. This is precisely why it fits teams or clients who need change to be gradual and evidence-driven rather than disruptive.

## Example

A five-person client-services team is chronically behind: everyone is "busy," yet almost nothing ships on time, and nobody can say what's actually stuck versus genuinely in progress. Visualizing the workflow reveals the real picture: 14 items are simultaneously "in progress" across five people — nearly three each — with several untouched for over a week. Introducing a WIP limit of 2 per person immediately makes the overload visible and forces prioritization: staff must finish or explicitly pause an item before pulling a new one, rather than starting everything at once. Within a month, cycle time per item drops by more than half, not because anyone worked harder, but because less was being started in parallel and more was reaching "done" per week — the classic Kanban result: throughput improves by constraining starts, not by adding people.

## Applying it for a client

Before recommending any tool (a Kanban board, project-management software), diagnose whether the client's real problem is *visibility* (nobody can see the work) or *overload* (too much is started at once) — a board without a WIP limit only solves the first problem and leaves the second, more damaging one untouched. Introduce TQM's cultural commitments gradually and specifically: ask where quality is currently only checked at the end of a process, and work backward to find where it could instead be built into an earlier step. For a client resistant to "another methodology," lead with Kanban's own selling point — it doesn't require adopting new roles or a big-bang process change, only visualizing what already happens and then constraining it — which tends to lower the resistance any consultant meets when proposing operational change.

## Watch-outs

- A Kanban board with no WIP limit is just a visual to-do list — the WIP limit is the mechanism that actually changes behavior and flow; a client who "does Kanban" without one hasn't adopted the part that matters.
- TQM without genuine leadership commitment collapses into posters and slogans — "quality is everyone's job" said once in a meeting does not change how defects are actually handled the next time one occurs.
- WIP limits set too generously (e.g., 8 per person) don't create the forcing function that makes overload visible — the limit has to be tight enough to occasionally hurt, or it isn't doing its job.
- Cumulative flow diagrams and cycle-time tracking require some minimum volume of recurring, similar work to be meaningful — a team doing one-off custom projects (job production) won't get useful signal from flow metrics the way a team running repeatable work does.
- "Continuous improvement" as a TQM value is easy to endorse and easy to let lapse without a recurring review cadence — anchor it to an actual meeting on the calendar, not an aspiration.

## Related

- [lean-six-sigma.md](../operations/lean-six-sigma.md) — Kanban's pull-based, waste-conscious origin is the same Toyota Production System that produced Lean; TQM and Six Sigma share the same quality-movement lineage.
- [theory-of-constraints.md](../operations/theory-of-constraints.md) — Kanban's WIP limits function like a practical Drum-Buffer-Rope mechanism, keeping upstream work from piling up ahead of a constraint.
- [iso-9001-qms.md](../operations/iso-9001-qms.md) — ISO 9001's seven principles and PDCA cycle are TQM's philosophy formalized into an auditable, certifiable standard.
- [sops-and-sipoc.md](../operations/sops-and-sipoc.md) — Kanban's "make policies explicit" practice is the same discipline SOPs apply at a more formal, documented level.
