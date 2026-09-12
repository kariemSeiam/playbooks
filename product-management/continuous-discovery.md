---
domain: product-management
concept: Continuous Discovery (Opportunity Solution Tree)
source: research — Teresa Torres ("Continuous Discovery Habits", 2021) / Product Talk
tags: [discovery, customer-research, validation, product-trio]
---

# Continuous Discovery (Opportunity Solution Tree)

Continuous discovery is the habit of the product trio (PM, design, engineering) touching real customers — through interviews, usability tests, or support-signal review — at least once every week, indefinitely, rather than treating discovery as a phase that finishes before a project starts. The Opportunity Solution Tree (OST) is the visual structure that keeps that ongoing research anchored to one desired outcome instead of sprawling into a disconnected pile of feature requests. Teresa Torres, a product discovery coach, developed and taught the technique from around 2016 onward and formalized it in her 2021 book. A consultant needs it because "we did user research before this project" is not the same claim as "we know, this week, whether what we're building is still right" — and most teams' discovery process is the former.

## When to use

- Discovery currently only happens in occasional standalone research sprints, disconnected from delivery, and the backlog is filling with stakeholder-requested features never traced back to a real customer problem.
- A team has a clear desired outcome (often an OKR Key Result — see [okrs.md](okrs.md)) but no structured way to generate and compare competing ways to achieve it.
- Justifying why a team is testing 3 small, cheap experiments before committing engineering weeks to build one full solution.
- A PM/design/engineering trio needs a shared visual artifact to have prioritization arguments on, instead of debating a flat, unstructured feature list.
- As the operating rhythm underneath a Now-Next-Later roadmap (see [now-next-later-roadmap.md](now-next-later-roadmap.md)) — the tree is where "Next" and "Later" bets get vetted before being promoted to "Now."

## How it works

### The habit: weekly customer touchpoints

Torres's baseline rule: the product trio has direct customer contact — interviews, usability tests, or support-ticket review — at least once a week, every week, indefinitely. Not a discrete phase. The goal is a continuous, small-batch stream of qualitative signal so decisions are never more than a week stale.

### The Opportunity Solution Tree — four layers, root to leaf

1. **Desired Outcome** (root) — the business or product outcome the trio owns, ideally a measurable OKR-style Key Result (e.g., "Increase week-4 retention from 22% to 30%"). One tree per outcome.
2. **Opportunities** (branches) — customer needs, pains, or desires — surfaced through interviews — that, if addressed, would move the desired outcome. Opportunities must be framed as customer problems, not solutions ("Customers don't trust automated categorization," not "Add a manual override button"). They can nest into sub-opportunities, and are plotted on an **Opportunity Map** scoring each for size (how many customers) and impact on the outcome — this is how the trio decides which branch to pursue next.
3. **Solutions** (next level) — multiple competing ideas for addressing one chosen opportunity. Torres recommends generating at least 3–4 divergent solutions per opportunity in parallel before converging on one — converging on the team's first idea is the most common failure this layer exists to prevent.
4. **Assumption Tests** (leaves) — the smallest testable assumption each solution depends on, surfaced via **Assumption Mapping** along two axes: Importance (how critical to the solution working) and Evidence (how much already supports it). High-importance, low-evidence assumptions get tested first and cheaply — fake-door tests, concierge tests, prototype interviews, or a small controlled experiment (see [experimentation-ab-testing.md](experimentation-ab-testing.md) for the mechanics of running the test itself).

### Interviewing technique that feeds the tree

Story-based interviewing ("tell me about the last time you...") beats hypothetical questions ("would you use a feature that...") because customers are unreliable narrators of their own future behavior but decent narrators of a specific past event. Every interview is logged into a running, shared **Interview Snapshot** so opportunities accumulate evidence over time instead of evaporating once the interview ends.

### Continuous vs. one-off discovery

| | One-off discovery sprint | Continuous discovery |
|---|---|---|
| Cadence | Before a project starts, then stops | Weekly, ongoing, indefinite |
| Output | A requirements doc / feature list | A living Opportunity Solution Tree |
| Trio involvement | Often research-team-only; findings handed to PM | PM + design + engineering all present in interviews |
| Risk reduced | Whether the *problem* is real (once) | Whether the *problem* and every candidate *solution* are real (continuously) |

## Example

A subscription meal-kit product's trio owns the outcome "increase week-4 retention from 22% to 30%." Weekly interviews surface an opportunity: "Customers feel overwhelmed by too many recipe choices and default to skipping a week." The trio maps two sibling opportunities beneath it (decision fatigue vs. delivery-timing mismatch) and, via the opportunity map, picks decision fatigue as higher-size and higher-impact. Under that opportunity they generate four candidate solutions: a "surprise me" default box, a saved-favorites quick-reorder, a 3-question weekly quiz, and a "skip this decision, repeat last week" button. Assumption mapping flags "repeat last week" as highest-importance/lowest-evidence — the team isn't sure customers want repeats rather than just fewer choices — so that assumption is tested first, via a 2-week fake-door test (button shown, clicks tracked, no repeat-order logic actually built yet) before any engineering time is committed to building it for real.

## Applying it for a client

Install the weekly-touchpoint habit before introducing the tree artifact itself — a client team not yet talking to customers weekly will produce a tree with guesses on it labeled as opportunities. Insist all three trio roles sit in on interviews, even briefly — the value isn't research-team efficiency, it's that engineering hears the "why" firsthand and stops treating discovery findings as someone else's opinion to argue with later. Build the tree live with the client trio in a workshop (a whiteboard or a tool like Miro) — the point is the trio doing the mapping and having the prioritization argument out loud on the artifact together, not a consultant handing over a finished tree. For a client already running OKRs, anchor the tree's root directly to the current period's Key Result — this is the cleanest way to show a client that "the roadmap" and "the research" are one conversation, not two separate documents.

## Watch-outs

- A tree with no live, currently-owned desired outcome at the root is just a mind map — the outcome must be real and measurable or the whole exercise loses its prioritization function.
- Generating only one solution per opportunity defeats the purpose — Torres is explicit that converging too fast on the first idea is the single most common failure, because the trio never sees the alternative that would have tested a risky assumption more cheaply.
- Treating "Opportunities" as a dump for every stakeholder feature request — an item phrased as a solution ("add SSO") doesn't belong at that layer; push the team to state the underlying customer need first ("enterprise buyers don't trust us with credential management").
- Weekly touchpoints can decay into a checkbox ritual (a rushed 15-minute call logged just to hit quota) — the habit only produces value if interviews are genuinely story-based and findings actually get logged onto the tree, not just held in someone's memory.

## Related

- [jobs-to-be-done.md](../product-management/jobs-to-be-done.md) — JTBD switch interviews are a strong source of "Opportunities" for the tree; the two techniques compose well.
- [okrs.md](../product-management/okrs.md) — the tree's root (Desired Outcome) should be a live Key Result, not an invented goal.
- [experimentation-ab-testing.md](../product-management/experimentation-ab-testing.md) — Assumption Tests at the tree's leaves are executed using the experimentation mechanics described there.
- [product-operating-model.md](../product-management/product-operating-model.md) — continuous discovery is the discovery-side habit of the empowered product trio described in that note.
