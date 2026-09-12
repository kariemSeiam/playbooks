---
domain: operations
concept: Lean Six Sigma
source: research — Toyota Production System (Ohno, 1988); Motorola Six Sigma (Smith, 1986); Womack & Jones, Lean Thinking (1996)
tags: [lean, six-sigma, dmaic, waste, quality, continuous-improvement]
---

# Lean Six Sigma

Lean Six Sigma is the merger of two separate improvement disciplines that were developed independently and later fused because they solve complementary problems. **Lean** comes out of the Toyota Production System — built by Taiichi Ohno and Shigeo Shingo at Toyota from the 1950s onward, and named/popularized for Western audiences by James Womack and Daniel Jones in *The Machine That Changed the World* (1990) and *Lean Thinking* (1996) — and its target is waste: anything a customer would not want to pay for if they could see it happening. **Six Sigma** was developed by engineer Bill Smith at Motorola in 1986 as a statistical method for reducing defects, and was popularized industry-wide when Jack Welch made it mandatory at General Electric in the mid-1990s; its target is variation: the inconsistency in a process's output that makes quality unpredictable. A consultant needs both halves together because a fast process that produces inconsistent output, or a consistent process that is needlessly slow and wasteful, are both failures — and each discipline alone only catches one of the two.

## When to use

- A client's process is slow, has long queues or backlogs, or carries visible non-value-adding steps (rework, excess motion, waiting) — start with Lean.
- A client's output is inconsistent — quality complaints, defect rates, or variable cycle times that make promises to customers unreliable — start with Six Sigma.
- A client wants a structured, evidence-based improvement project rather than an ad-hoc fix, and needs a defensible before/after case to justify the investment.
- Diagnosing why a previous "improvement" initiative stalled — very often it optimized one dimension (speed) while ignoring the other (consistency), or vice versa.
- Any recurring quality or throughput problem where the client has data (or could easily start collecting it) but hasn't structured an analysis around it.

## How it works

### DMAIC — the five-phase improvement cycle

DMAIC is Six Sigma's operating structure, and Lean Six Sigma runs Lean's waste-elimination tools inside the same five phases rather than as a separate process.

| Phase | Goal | Typical tools |
|---|---|---|
| **Define** | Scope the problem, the process boundaries, and the customer requirement at stake. | SIPOC diagram, project charter, Voice of the Customer (VOC) |
| **Measure** | Establish a factual baseline — how the process currently performs, with real data, not opinion. | Process mapping, data collection plan, measurement system analysis |
| **Analyze** | Find the root cause(s) of the defect or waste, statistically or structurally. | Value stream mapping, Pareto analysis, root-cause (fishbone) diagrams, hypothesis testing |
| **Improve** | Design and pilot a fix that addresses the verified root cause, not just the symptom. | Kaizen events, process redesign, pilot testing, mistake-proofing (poka-yoke) |
| **Control** | Lock in the gain so the process doesn't drift back to its old baseline. | Control charts, updated SOPs, ongoing monitoring dashboards |

The discipline of DMAIC is that a team is not allowed to jump straight to "Improve" — the two most commonly skipped phases (Measure and Analyze) are exactly the ones that separate a real fix from a guess.

### The eight wastes (Lean's target)

Lean names eight categories of non-value-adding activity. Two common acronyms encode the same eight items in different orders — DOWNTIME and TIMWOODS — and both are worth knowing since clients and other consultants use either:

| Waste | DOWNTIME | TIMWOODS | What it looks like in practice |
|---|---|---|---|
| Defects | D | D | Output that must be scrapped, reworked, or apologized for |
| Overproduction | O | O | Making more/sooner than the next step or customer actually needs |
| Waiting | W | W | Idle time between steps — a person, batch, or machine waiting on the next input |
| Non-utilized talent | N | S (Skills) | Underusing people's knowledge, ideas, or skills |
| Transportation | T | T | Moving materials or information further than necessary |
| Inventory | I | I | Excess stock, WIP, or backlog sitting unused |
| Motion | M | M | Unnecessary physical or digital movement by people doing the work |
| Extra-processing | E | O (Overprocessing) | Doing more work, or a higher precision, than the customer actually values |

"Non-utilized talent" is the one waste Toyota's original seven did not include — it was added later specifically because knowledge-work and service processes lose as much value to under-used people as manufacturing loses to physical waste.

### Value stream mapping

A value stream map draws every step a product or request passes through, end to end, and labels each step as value-added or non-value-added from the customer's point of view, with the wait time between steps shown explicitly. The output that matters is a single number: the ratio of value-added time to total lead time. In most unoptimized service processes this ratio is shockingly low — a request that takes ten value-added minutes can easily sit inside a five-day total lead time, and the nine-plus days of waiting is exactly what the map is built to expose and target.

### Kaizen

Kaizen (Japanese for "continuous improvement") is Lean's cultural mechanism for sustaining gains: small, frequent, incremental improvements driven by the people who do the work, rather than large infrequent projects driven only by management or outside consultants. A "Kaizen event" is a focused, time-boxed (often 3-5 day) workshop where a cross-functional team maps a specific process, identifies waste, and implements a fix on the spot rather than filing a recommendation for later.

### Six Sigma's statistical target

"Six Sigma" refers to a process so tightly controlled that its output falls within six standard deviations of the mean before a defect occurs — in practice, this is operationalized as 3.4 defects per million opportunities (DPMO). The sigma table shows how dramatically defect rates change per level:

| Sigma level | DPMO (approx.) | Practical read |
|---|---|---|
| 2σ | 308,000 | Most unmanaged processes sit here or worse |
| 3σ | 66,800 | "Good enough" for many small businesses |
| 4σ | 6,210 | Typical for a well-run, unoptimized process |
| 5σ | 233 | High-performing process |
| 6σ | 3.4 | World-class; rarely needed outside safety-critical or very high-volume operations |

### Belt structure

Six Sigma borrows a martial-arts-style certification hierarchy that is useful for a consultant to recognize on a client's org chart or resume: **Yellow Belt** (basic awareness, supports projects), **Green Belt** (leads smaller projects part-time alongside a regular job), **Black Belt** (leads major projects full-time, trains Green Belts), **Master Black Belt** (trains Black Belts, sets improvement strategy org-wide). Most small and mid-size clients never need anything past Green Belt-level rigor to get real value.

## Example

A client running a document-processing back office has a 6-day average turnaround and a 12% error rate on submitted forms. Running DMAIC: **Define** — scope is "form intake to approval," customer requirement is "under 2 days, error-free." **Measure** — the team times every step for two weeks and finds the actual hands-on processing time is 45 minutes; the rest of the 6 days is queue-waiting between four handoffs. **Analyze** — a Pareto chart of the error causes shows 70% of errors trace to one ambiguous field on the intake form, not to processor mistakes. **Improve** — the form is redesigned (removing the ambiguous field) and one redundant handoff is eliminated via a Kaizen event. **Control** — a control chart tracks weekly error rate and turnaround, with an owner accountable if either drifts back up. Result: turnaround drops from 6 days to under 2, and error rate from 12% to under 2% — and critically, both numbers were fixed together, because fixing only the queue (Lean) would have left the ambiguous-field defect untouched, and fixing only the form (Six Sigma) would have left the four-handoff queue untouched.

## Applying it for a client

Never let a client (or a junior consultant) skip straight from a complaint to a fix — run the Define and Measure phases explicitly, even in compressed form, because the single most common failure in improvement work is "solving" a problem the data doesn't actually support. Use value stream mapping as the fastest way to get a client's own eyes on their waste — most founders and operators have never seen their own process's value-added ratio laid out visually, and the map itself often generates more buy-in for change than any argument you could make. Match the rigor to the stakes: a two-person startup's process rarely needs formal DPMO tracking or belt-certified staff, but it always benefits from the DMAIC discipline of measure-before-you-fix and control-after-you-fix. And always pair the two halves — ask "is this process slow (Lean problem), inconsistent (Six Sigma problem), or both" before choosing which toolkit to lead with.

## Watch-outs

- Don't apply Six Sigma's full statistical machinery (control charts, hypothesis testing, DPMO tracking) to a low-volume, low-stakes process — the overhead of measurement can exceed the value of the fix for a small operation.
- "Kaizen" is easy to say and hard to sustain — without a named owner and a recurring cadence, the "continuous" part quietly stops after the first event.
- A value stream map is only as honest as the timing data behind it — don't let a client estimate step durations from memory when actual timestamped data is available; memory systematically underestimates wait time.
- Non-utilized talent is the waste most often ignored in a mapping exercise because it doesn't show up as a visible delay or defect — deliberately ask the team doing the work what they'd change, not just where the paper trail sits idle.
- Improvement gains that aren't locked in with a Control-phase mechanism (a metric, an owner, a review cadence) reliably erode back toward baseline within months — "we fixed it" without a control mechanism is not actually done.

## Related

- [sops-and-sipoc.md](../operations/sops-and-sipoc.md) — SIPOC is the standard scoping tool used in DMAIC's Define phase.
- [theory-of-constraints.md](../operations/theory-of-constraints.md) — a complementary lens: TOC asks which single bottleneck limits throughput, which sometimes redirects where a Lean Six Sigma project should even start.
- [tqm-and-kanban.md](../operations/tqm-and-kanban.md) — Kanban descends from the same Toyota Production System that produced Lean; both are pull-based, waste-conscious systems.
- [production-processes.md](../operations/production-processes.md) — DMAIC and value stream mapping are the concrete tools for diagnosing the cost/lead-time/quality problems described there.
