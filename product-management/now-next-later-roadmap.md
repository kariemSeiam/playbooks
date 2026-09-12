---
domain: product-management
concept: Now-Next-Later Roadmap
source: research — Janna Bastow (ProdPad) + Josh Seiden, "Outcomes Over Output" (2019)
tags: [roadmap, planning, outcomes, commitment]
---

# Now-Next-Later Roadmap

A Now-Next-Later roadmap organizes work into three loose time horizons instead of a date-based Gantt chart or a quarter-by-quarter release schedule — deliberately trading date-precision for commitment-honesty: it communicates relative priority and confidence without implying a delivery date the team can't actually guarantee. Janna Bastow, co-founder of the roadmapping tool ProdPad, originated the format as a reaction to how dated roadmaps get treated as broken promises the moment reality shifts (which, on anything further out than a sprint or two, is most of the time); the outcome-over-output principle that should populate each column comes from Josh Seiden's writing, which argues roadmap items should be framed as outcomes to achieve, not features to ship. A consultant needs this distinct from the "Now/Next/Later" categorization inside [prioritization-techniques.md](prioritization-techniques.md) — that one buckets individual features by urgency; this is a full roadmap *format*, built around outcomes and honest uncertainty.

## When to use
- A client's current roadmap is a dated Gantt or release schedule that keeps "breaking" — treated as a promise, then causing trust damage with stakeholders every time a date slips.
- Communicating a roadmap to external stakeholders (customers, the board, partners) who need relative priority and direction without being given a commitment the team can't defend under real uncertainty.
- Early-stage or fast-moving products where specific dates 2+ quarters out are close to fictional — the format is designed to be honest about that uncertainty instead of hiding it behind false precision.
- Pairing with OKRs ([okrs.md](okrs.md)) — the Now column should map to the current cycle's committed OKRs; Next and Later hold candidate outcomes not yet committed to.

## How it works

### The three columns — defined by confidence, not calendar dates
- **Now** — what the team is actively working on this cycle. High confidence, high commitment — effectively the current sprint or quarter's committed work, validated and resourced. Roughly equivalent to a Scrum team's current Sprint/Release Backlog, but framed at outcome-level rather than task-level.
- **Next** — what's coming after Now, directionally clear but not yet locked into a specific solution or exact timing. Medium confidence — validated as a priority, not yet fully scoped or committed to a delivery window. This is where an Opportunity Solution Tree's validated-but-unbuilt branches typically live (see [continuous-discovery.md](continuous-discovery.md)).
- **Later** — ideas and directions being watched or explored, not yet validated enough to commit real resources to. Low confidence, explicitly provisional — items here are expected to move, get cut, or get reshaped as more is learned; nobody outside the team should treat a Later item as a promise.

### The outcome-over-output principle
Each roadmap item should be framed as a problem to solve or an outcome to move ("Reduce time-to-first-value for new teams"), not a feature to ship ("Build a new onboarding wizard"). This matters specifically because a feature-framed item has already made a solution decision before discovery has happened — an outcome-framed item leaves the solution to be discovered by the team (see [continuous-discovery.md](continuous-discovery.md), [product-operating-model.md](product-operating-model.md)), and survives a pivot in approach without needing to be rewritten.

### Comparison with a date-based (Gantt) roadmap
| | Gantt / date-based roadmap | Now-Next-Later |
|---|---|---|
| Precision | Specific dates, specific features | Relative horizon, outcome-framed |
| Reads to stakeholders as | A commitment/contract | A current best estimate of priority and direction |
| What breaks trust | Any date slip (routine, and treated as a broken promise) | Nothing structurally "breaks" — items are expected to move between columns as validation changes |
| Best suited to | Highly predictable, low-uncertainty delivery (rare in product work) | Genuinely uncertain, discovery-driven product work (most product work) |
| Failure mode | False precision — hides real uncertainty until it surfaces as a missed date | Can be used to dodge real accountability if "Now" items are never actually delivered either |

### Operating cadence
Review and re-sort the three columns on a regular cadence, commonly aligned to the OKR/quarterly cycle — items move Later → Next → Now as discovery validates them (or get cut entirely), and Now items graduate off the roadmap once shipped and measured. The roadmap is a living, constantly re-sorted artifact, not a document finalized once per planning cycle and left static.

## Example

A B2B analytics product's Now-Next-Later roadmap, framed outcome-first:
- **Now:** "Reduce time-to-first-dashboard for new admins from 6 days to 2 days" — this quarter's committed OKR Key Result; a specific onboarding-flow redesign is already in build, discovered via continuous discovery.
- **Next:** "Increase weekly active dashboard viewers per account" — validated as a priority via interviews revealing dashboards are built once and rarely revisited, but the specific solution (scheduled email digests, Slack alerts, or an in-app nudge) hasn't been decided, pending assumption testing.
- **Later:** "Explore whether an API/webhook layer for automated consumers of dashboard data is worth building" — a direction the team is watching given early customer signals, not yet validated enough to commit discovery time to, let alone build.

Six weeks later, "Next" resolves: interviews plus a fake-door test show scheduled email digests decisively beat Slack alerts for this customer base, so that item moves to "Now" with a specific committed scope, while the API/webhook item stays in "Later," unpromoted, because customer signal hasn't strengthened yet.

## Applying it for a client

Convert an existing dated Gantt roadmap into Now-Next-Later as a trust-repair exercise when a client's stakeholders have stopped believing roadmap dates — reframe "Q3: ship feature X" as "Now: reduce [metric] via [problem space]," stripping the false-precision date while keeping the priority signal intact. Insist every item, in every column, is written as an outcome or problem, not a feature name — this is the step clients most often skip, defaulting back to a feature list with three columns slapped on top, which loses the entire benefit of leaving solution-space open for discovery. Tie the Now column explicitly to the current period's OKRs ([okrs.md](okrs.md)) so the roadmap and the goal-setting process are one conversation, not two documents the client has to reconcile manually. For external audiences (customers, board), Now-Next-Later is usually the safer format to share than an internal Gantt chart with dates — it communicates direction and momentum without exposing the team to blame for the routine date-slips a more detailed internal plan will still experience.

## Watch-outs

- The format doesn't eliminate the need for real prioritization discipline — a team can dump nearly everything into "Next" to avoid hard choices about what's actually validated; the same rigor from [prioritization-techniques.md](prioritization-techniques.md) still needs to decide what earns a column, not just how it's labeled.
- "Now" items can quietly become a fixed date-based commitment in disguise if a team keeps something in "Now" for many cycles without shipping — the format's honesty depends on items actually moving (or getting cut), not accumulating in the first column indefinitely.
- Stripping dates entirely can go too far for stakeholders (finance, sales making customer commitments) who genuinely need to plan around approximate timing — pair the Now-Next-Later view with a separate, clearly-labeled rough-timing indicator for those audiences rather than refusing to give any time signal at all.
- The outcome-over-output principle is the part clients resist most, because "we're building X" is easier to say and sounds more concrete than "we're trying to move Y" — hold the line on outcome framing especially in the Now and Next columns, since those are the ones about to consume real resources.

## Related

- [okrs.md](../product-management/okrs.md) — the Now column should map directly to the current period's committed Key Results.
- [continuous-discovery.md](../product-management/continuous-discovery.md) — items typically move Later → Next → Now as the Opportunity Solution Tree's assumption tests validate them.
- [product-roadmap.md](../product-management/product-roadmap.md) — Now-Next-Later is one specific format among the roadmap types that note catalogs; this note is the deeper mechanism behind the lightweight, outcome-honest alternative to a dated roadmap.
- [prioritization-techniques.md](../product-management/prioritization-techniques.md) — NNL as a prioritization bucket (categorizing individual features by urgency) is a related but distinct use of the same three labels; this note is the roadmap-format version, built around outcomes and commitment-honesty rather than per-feature urgency sorting.
