---
domain: people-org
concept: OKRs for Organizational Execution
source: research — Andy Grove, "High Output Management" (1983); John Doerr, "Measure What Matters" (2018)
tags: [goal-setting, alignment, execution, cascade, quarterly-planning]
---

# OKRs for Organizational Execution

The mechanism itself — what an Objective and a Key Result are, who built it and why, the committed-vs-aspirational distinction — is [okrs.md](../product-management/okrs.md)'s job; this note doesn't re-derive it. What's distinct here is the organizational layer on top of that mechanism: a consultant reaches for OKRs at this level not to track a single team's output but to force every layer of a company to state, in public and in numbers, what "progress this quarter" actually means, and then cascade that definition downward so team priorities don't silently drift from company strategy. It is one of the most battle-tested execution frameworks in existence, adopted at Google, Intel, LinkedIn, Spotify, and thousands of scale-ups since Grove built it at Intel and Doerr carried it to Google in 1999.

## When to use

- A company has an annual strategy but no repeatable mechanism to translate it into what teams actually work on this quarter.
- Multiple teams' priorities have drifted out of alignment with each other, or the CEO can't explain what three teams are doing and why it matters.
- Leadership wants to shift culture from safe, easily-hit targets toward ambitious, stretch behavior — and needs a scoring system that rewards the attempt, not just the hit.
- The org has KPIs for steady-state health but nothing that names what specifically needs to *change* this cycle.
- Right after an annual strategy or planning offsite, before quarterly execution begins — OKRs are the translation layer between the offsite's decisions and Monday morning's work.

## How it works

### Anatomy of one OKR

| Part | Definition | Test |
|---|---|---|
| **Objective** | A qualitative, ambitious, time-bound statement of direction. Memorable, not a number. | Would this energize the team, or is it just a target dressed as a sentence? |
| **Key Results** (3-5 per Objective) | Quantitative, verifiable metrics that prove the Objective is being achieved. | Can you grade it 0-100% with no argument about interpretation? If it's a task ("launch the redesign") not a measurable outcome ("increase activation rate from 40% to 55%"), it's not a real KR. |

### The cascade: company → team → individual

OKRs work as a nested translation, not a copy-paste chain:

1. **Company OKRs** — set annually by the leadership team, revisited and re-scored quarterly. These are the 3-5 things that matter most for the business this year.
2. **Team OKRs** — set quarterly. Teams don't inherit company KRs verbatim; they draft their own Objective and KRs that plausibly *ladder up* to a company KR, informed by what only they know about their function. This bottom-up drafting against a top-down direction is what Doerr calls OKRs' "70% top-down, 30% bottom-up" balance — pure top-down produces compliance, not ownership.
3. **Individual OKRs** (optional) — many mature orgs, including Google in later years, drop this level entirely. Individual OKRs are the most prone to being used as disguised performance-review inputs, which destroys the honesty the whole system depends on (see Watch-outs).

### Committed vs. aspirational OKRs

Google's practice distinguishes two kinds, and conflating them is the single most common implementation failure:

- **Committed OKRs** — resourced, expected, and must hit 1.0. Missing one is a planning failure to investigate (e.g., "ship the new billing system").
- **Aspirational (stretch) OKRs** — deliberately set beyond what current resources guarantee. Landing at 0.6-0.7 is success, not a miss.

### Grading

Score each Key Result 0.0-1.0 based on actual measured progress, then average the KRs for an Objective score.

| Score | Reading |
|---|---|
| 1.0 | Fully hit. For an aspirational OKR, this usually means it was sandbagged — set too low. |
| 0.7 | Google's stated sweet spot for aspirational OKRs: real stretch, real progress, not a comfortable target. |
| 0.4-0.6 | Meaningful progress but a clear miss — worth a retro on why (wrong KR, under-resourced, external shock). |
| < 0.3 | Either badly under-resourced, badly designed, or a signal the Objective itself was wrong. |

### Cadence

| Level | Set | Reviewed |
|---|---|---|
| Company | Annually | Quarterly scoring + light revision |
| Team | Quarterly | Weekly check-ins (informal progress, blockers) |
| Individual (if used) | Quarterly | Weekly, folded into 1:1s |

### OKRs vs. KPIs

KPIs are health metrics — they tell you the business-as-usual engine is still running (churn rate, uptime, NPS) and you maintain them. OKRs are change metrics — they name what specifically has to move this quarter that isn't moving on its own. A KPI dashboard and an OKR list should coexist; a common failure is turning steady-state KPIs into OKRs simply because they're already measured, which produces "objectives" nobody is actually stretching for.

## Example

**Company Objective (annual, aspirational):** "Become the most trusted logistics partner for SME merchants in Egypt."

- KR1: Net Promoter Score among SME merchants from 32 → 55.
- KR2: On-time delivery rate from 88% → 96%.
- KR3: Merchant churn (quarterly) from 9% → 4%.

**Operations team OKR (Q3, laddering to KR2 above):**

- Objective: "Make late deliveries the exception, not the norm."
- KR1: Reduce average last-mile delay from 4.1 hrs to 1.5 hrs.
- KR2: Cut route-planning errors flagged by drivers from 120/week to 30/week.
- KR3: Roll out the new dispatch algorithm to 100% of hubs (committed, not aspirational — this one must hit 1.0).

At quarter end, Operations scores 0.65 on KR1, 0.8 on KR2, 1.0 on KR3 (committed KR fully delivered) — Objective score 0.82, a strong quarter, distinct from a company-level KR2 that might land at 0.55 because on-time delivery depends on more than Operations alone (weather, courier partners, warehouse handoffs).

## Applying it for a client

Start with company OKRs, and refuse to let the client skip straight to team-level goal-setting — without a stated company Objective, every team's KRs are laddering to nothing, and you'll spend the next two quarters mediating priority conflicts that a shared Objective would have prevented. When a client is new to OKRs, run one quarter with committed OKRs only (skip aspirational) so the team learns the scoring discipline without the confusion of a "70% is a win" mindset landing on top of "we've never done this before." Watch the first grading session closely: if every team scores 0.9+ across the board, the KRs were sandbagged, not achieved — that's the moment to reset expectations before the pattern calcifies. For a founder-led company under ~30 people, skip individual OKRs entirely and stop at team level — the overhead of a third cascade layer outweighs the alignment benefit until the org is big enough that a CEO can no longer see everyone's work directly.

## Watch-outs

- Tying OKR scores directly to compensation or performance reviews destroys the system — people will only set OKRs they're certain to hit, and the entire aspirational-stretch mechanism collapses into safe target-setting.
- A Key Result that's actually a task ("redesign the checkout flow") rather than a measurable outcome ("increase checkout completion from 61% to 75%") can't be honestly graded — it either happened or didn't, with no signal about whether it worked.
- More than 3-5 Objectives per level signals the org hasn't actually prioritized — it's just relabeled the entire backlog as "objectives."
- Setting team OKRs as pure top-down copies of company KRs produces compliance, not ownership; teams need real room to draft their own path to the shared outcome.
- Skipping the weekly check-in cadence is the most common silent failure — OKRs set once a quarter and never revisited become a document nobody remembers by month two.

## Related

- [okrs.md](../product-management/okrs.md) — the product-scoped version of OKRs (feature and roadmap-level goal-setting); this note is the company/team execution layer it sits inside.
- [raci-rapid-daci.md](raci-rapid-daci.md) — once an OKR names what needs to happen, RACI/RAPID/DACI names who actually decides and who executes it.
- [org-design-star-model.md](org-design-star-model.md) — the Rewards point of the Star Model is exactly where OKR-compensation entanglement (see Watch-outs) gets designed in or out.
