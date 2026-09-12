---
domain: product-management
concept: Objectives & Key Results (OKRs)
source: research — Andy Grove ("High Output Management", 1983) → John Doerr ("Measure What Matters", 2018)
tags: [goal-setting, alignment, execution, strategy]
---

# Objectives & Key Results (OKRs)

OKRs pair a qualitative, inspiring Objective (the "what") with 2–5 quantitative, verifiable Key Results (the "how we'll know we got there"). Andy Grove invented the framework at Intel as "iMBOs" (Intel Management by Objectives); John Doerr, who had worked under Grove at Intel as a young salesman, brought it to Google in 1999, and later popularized it industry-wide with his 2018 book. A consultant needs it as the mechanism that turns a strategy statement into a small number of falsifiable commitments for a defined period — the alternative, in practice, is a roadmap that says "ship faster" and can't be checked against anything at quarter-end.

## When to use
- Quarterly (sometimes annual) planning cycles, when leadership needs to translate strategy into a small number of measurable near-term bets.
- Cross-functional alignment — giving multiple teams traceable line-of-sight from a company objective down to team-level key results without micromanaging *how* each team gets there.
- Replacing a vague roadmap ("ship faster," "improve quality") with a falsifiable commitment ("reduce median time-to-first-value from 14 days to 5 days").
- A team is running too many initiatives at once and needs forced prioritization — OKRs work specifically because they cap what gets committed to.
- Cross-domain use: the same mechanic underlies goal-setting and performance-alignment processes on the people/organization side — same tool, different owner, worth naming when a client asks how OKRs relate to individual performance reviews (they shouldn't be the same thing — see Watch-outs).

## How it works

### Anatomy
- **Objective** — qualitative, ambitious, time-bound, and memorable. ("Delight our power users," not "Improve engagement.")
- **Key Results** — 2–5 per objective, quantitative, specific, and independently verifiable at period-end. ("Increase weekly-active-to-paid conversion from 8% to 12%," not "Improve conversion.")

Grove's own test for whether an Objective/KR pair is well-formed: the Objective answers "Where do I want to go?"; the Key Results answer "How will I pace myself to see if I'm getting there?"

### Committed vs. aspirational (stretch) OKRs
Google's own distinction, worth carrying into any client engagement:
- **Committed OKRs** — agreed to be achieved at 100%, and resourced accordingly. Missing one is treated as a planning failure, not just bad luck.
- **Aspirational/stretch OKRs** — deliberately set so the team is expected to land around 0.6–0.7 on average. Scoring 1.0 on a stretch OKR usually means it wasn't ambitious enough; scoring near 0 means either poor execution or a badly-designed Key Result.

### Scoring
Each Key Result is scored 0.0–1.0 (or 0–100%) at period-end based on actual measurement; the Objective's score is the average of its Key Results. Common color-coding: 0.7–1.0 green (on track/hit), 0.4–0.7 yellow (progress but at risk), 0–0.4 red (off track).

### Cascade — hybrid, not pure waterfall
Company OKRs → team/department OKRs → (optionally) individual OKRs — but this should not be a rigid top-down waterfall. Doerr, and later practitioners such as Christina Wodtke ("Radical Focus"), emphasize that roughly half of a team's OKRs should be proposed bottom-up by the team itself, not purely cascaded down, to preserve genuine ownership rather than compliance.

### Cadence
Quarterly is the minimum review rhythm; a weekly check-in (Wodtke's "Monday commit / Friday wins" pattern) is what actually keeps OKRs steering decisions in-quarter rather than becoming a document reviewed only at the end. OKRs set once at the start of a quarter and never revisited until scoring time is the single most common failure mode in practice.

### OKRs vs. KPIs vs. tasks
| | OKRs | KPIs | Tasks / to-dos |
|---|---|---|---|
| Purpose | An ambitious *push* into new territory, for a defined period | Ongoing health metrics that must stay within bounds | The actual work items that, if done, should move a Key Result |
| Time-bound | Yes — quarter or similar | No — continuously monitored | Yes — usually shorter than a quarter |
| "Achieved"? | Scored at period-end | Maintained, not "achieved" — a breach can itself become next quarter's OKR | Completed or not |
| Relationship | The goal | The guardrail | The means; completing all tasks ≠ hitting the KR |

## Example

Doerr's own book cites Larry Page's 1999 seed OKR for Google's Search team, built around specific search-quality and latency benchmarks — an early, concrete instance of the framework at the company where it became best known.

A more granular, numeric SaaS example built for a client engagement: **Objective — "Make onboarding effortless for new teams."**
- KR1: Reduce time-to-first-value from 9 days to 3 days.
- KR2: Increase week-1 activation rate from 35% to 55%.
- KR3: Reduce onboarding-related support tickets per 100 signups from 18 to 8.

End of quarter: KR1 lands at 4 days (score ≈ 0.83), KR2 lands at 48% (score ≈ 0.65), KR3 lands at 11 (score ≈ 0.70) → Objective score ≈ 0.73. That's a healthy stretch-OKR outcome — not a perfect 1.0 (which would suggest it wasn't ambitious enough), not a near-0 miss.

## Applying it for a client

Facilitate a hybrid top-down/bottom-up session: leadership proposes 2–3 company-level objectives; each team then drafts its own Key Results against those objectives, rather than having Key Results handed down whole. This single move is the highest-leverage way to prevent OKRs from becoming a top-down compliance exercise the team doesn't actually own. Cap objectives per team at 3–5 and Key Results per objective at 2–5 — a client's first draft is almost always 2–3x too long, and the cut needs to happen in the room, not left as homework. Separate the OKR-setting workshop from the scoring/retro meeting: set at the start of the period, do a lightweight midpoint check, then a full retro and rescore at period-end that also seeds the next cycle's OKRs. Anchor the top-level Objective's Key Results to a North Star Metric (see [north-star-metric.md](north-star-metric.md)) or the "Now" column of a live roadmap (see [now-next-later-roadmap.md](now-next-later-roadmap.md)) so OKRs aren't invented disconnected from what the team already tracks.

## Watch-outs

- **Sandbagging** — teams learn a low committed-OKR score reflects badly on them, so they quietly set easy Key Results to guarantee green. This defeats the entire stretch-goal purpose; explicitly decouple OKR scores from performance reviews and compensation to reduce the incentive (Google's own stated policy).
- **Activity-framed Key Results** — a KR phrased as an activity ("launch feature X") rather than an outcome ("increase metric Y") can be "achieved" even if the underlying metric never moves. Rewrite any KR that would still score 1.0 whether or not it actually worked.
- **Too many OKRs** — more than 3–5 objectives per team dilutes the framework back into an ordinary to-do list; the discipline *is* the cap.
- **Set-and-forget** — OKRs reviewed only at period-end, not weekly or biweekly, lose their steering function entirely; by the time an off-track Key Result is noticed, there's no runway left to correct course.
- **Confusing OKRs with KPIs** — treating a KPI breach (an ongoing health metric going out of bounds) as a "missed OKR" conflates "we didn't push far enough" with "something broke that should never have broken" — these need different responses.

## Related

- [north-star-metric.md](../product-management/north-star-metric.md) — the NSM commonly anchors the top company-level Objective's Key Result.
- [now-next-later-roadmap.md](../product-management/now-next-later-roadmap.md) — the roadmap's "Now" column should be resourced by, and traceable to, the current period's committed OKRs.
- [product-management-fundamentals.md](../product-management/product-management-fundamentals.md) — OKRs are one of the operating mechanisms that keeps the "build the right product" half of the job measurable rather than aspirational.
- [okrs-execution.md](../people-org/okrs-execution.md) — this note is the mechanism; that one is the organization-wide cascade and cadence built on top of it.
