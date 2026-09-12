---
domain: product-management
concept: Product Analytics & the HEART Framework
source: research — Kerry Rodden, Google (HEART framework, CHI 2010); Amplitude/Mixpanel behavioral-analytics practice
tags: [analytics, metrics, ux-quality, retention, cohorts]
---

# Product Analytics & the HEART Framework

HEART measures the quality of a user experience along five dimensions — Happiness, Engagement, Adoption, Retention, Task Success — developed at Google by researcher Kerry Rodden specifically because UX teams lacked a structured way to turn qualitative UX goals into trackable metrics at scale. This note pairs HEART with the behavioral-analytics techniques (cohort analysis, retention curves) that modern product-analytics tools like Amplitude and Mixpanel use to actually compute its Engagement and Retention dimensions from raw event data. A consultant needs this because a North Star Metric or a revenue number can rise while the underlying user experience quietly degrades for a segment — HEART is the checklist that catches that before it shows up as churn.

## When to use
- A UX or design decision needs a metric to be evaluated against, and the team's current metrics are all business/revenue numbers with no dimension capturing experience quality.
- Setting up a product-analytics instrumentation plan from scratch — HEART's Goals-Signals-Metrics grid is a structured way to decide what to track before writing any tracking code.
- Diagnosing a retention problem in specific detail — cohort retention curves show *when* in a user's lifecycle they drop off, which a single aggregate churn number can't reveal.
- Complementing a North Star Metric ([north-star-metric.md](north-star-metric.md)) — HEART's five dimensions are a checklist for UX-quality blind spots an NSM alone won't surface.

## How it works

### The five HEART dimensions
1. **Happiness** — subjective satisfaction; how users feel about the product. Measured via surveys (CSAT, NPS, in-product satisfaction prompts) — not behavioral event data alone, since satisfaction isn't directly observable from clicks.
2. **Engagement** — depth and frequency of user involvement, not just presence. Measured via behavioral events: frequency (sessions per week), intensity (actions per session), breadth (number of distinct features used).
3. **Adoption** — new users starting to use the product, or a specific feature. Measured via new-user or new-feature-usage counts within a defined period.
4. **Retention** — the rate existing users return / keep using the product (or a feature) over time. Measured via cohort retention curves (below) — the dimension most susceptible to a single vanity aggregate number hiding real churn.
5. **Task Success** — traditional usability metrics: efficiency (time to complete a task), effectiveness (% completing a task successfully), error rate. Measured via task-level funnels or in-lab usability testing, not aggregate engagement alone.

Rodden's own guidance: not every project needs all five dimensions instrumented. Pick the 2–3 most relevant to the specific feature or product goal being evaluated, rather than forcing all five onto every project.

### Goals-Signals-Metrics (GSM) — turning HEART into trackable metrics
For each relevant HEART dimension, work in this order:
1. **Goals** — state what you're trying to achieve for users in plain language ("Users should find search results relevant and be able to act on them quickly").
2. **Signals** — list the observable evidence, behavioral or attitudinal, that would indicate progress ("users click the first result and don't immediately re-search"; "users rate search helpfulness highly in a survey").
3. **Metrics** — turn each signal into something concretely trackable and comparable over time ("% of searches where the user clicks a result within 10 seconds and doesn't issue a new search in the next 60 seconds"; "average post-search CSAT score").

Working goal → signal → metric in that order specifically prevents the common failure of picking a metric first because it's easy to track (e.g., "let's track clicks") without establishing it actually signals progress toward a real UX goal.

### Cohort analysis and retention curves — the mechanics behind Retention
- A **cohort** is a group of users sharing a starting event, usually signup date (e.g., "users who signed up in the week of March 3"). Cohorting by acquisition date, rather than looking at all users in aggregate on a given calendar day, is what lets you compare like-for-like — a user in week 1 of their lifecycle should never be compared directly to a user in week 20 of theirs.
- A **retention curve** plots, for each cohort, the percentage still active at Day 1, Day 7, Day 30, Day 90, and so on after signup. The curve's *shape* matters more than any single point: a curve that keeps declining indefinitely (a "leaky bucket," never flattening) indicates the product hasn't found lasting value for any stable subset of users; a curve that flattens after an initial drop (the "smile curve," common in healthy retained products) indicates a core group has found durable value and the drop-off is mostly users who were never a fit.
- **Cohorting by behavior, not just signup date**, is the more diagnostic version — e.g., comparing the retention curve of users who completed a specific onboarding action in week 1 against those who didn't. This is usually how a team discovers its actual activation "aha moment" — the specific early action correlated with much better long-term retention.
- **N-day vs. bracket retention** — N-day retention (exactly active on day N) is noisier for low-frequency products; bracket retention (active at any point within a window, e.g., days 1–7) smooths that noise and is usually the more stable metric for products not used daily.

## Example

A note-taking app instruments HEART for a new "shared workspace" feature using GSM:
- **Adoption** — Goal: "users try the new shared workspace." Signal: "user creates or joins a shared workspace within their first week." Metric: "% of new signups creating/joining a workspace in week 1" — baseline 12%.
- **Engagement** — Goal: "shared workspaces become a regular part of a team's workflow." Signal: "the team edits it multiple times per week." Metric: "average edits per workspace per week" — baseline 3.1.
- **Retention** — Goal: "teams keep using the workspace past initial novelty." Metric: cohort retention curve of "% of workspaces still edited in week N," by creation week — the curve drops sharply from 100% (week 0) to 40% (week 2), then flattens near 38% through week 8: a smile curve indicating roughly 38–40% of created workspaces represent genuine, durable adoption.
- **Task Success** — Goal: "users can find and invite the right teammate without confusion." Metric: "% of invite attempts completed without error or abandonment." Usability testing surfaces a specific confusing step — searching by username fails silently if the teammate hasn't set one — that behavioral data alone hadn't flagged.
- **Happiness** — an in-product survey after a user's third workspace edit asks a 1–5 satisfaction question; the average is 4.1, but segmenting by whether the user hit the invite-search bug shows those users average 2.8 — tying a Task Success problem directly to a Happiness cost.

## Applying it for a client

Run the GSM exercise with the client's product/design team before writing a single analytics event — clients with existing analytics tools (Amplitude/Mixpanel already installed) very often have tracked whatever was easy (page views, generic clicks) rather than what actually signals progress toward a UX goal; GSM is the intervention that fixes this retroactively. For a client diagnosing a retention problem, insist on cohort-by-signup-week retention curves before accepting any single aggregate "our churn rate is X%" figure — the aggregate can hide a healthy smile-curve segment being dragged down by an unrelated leaky-bucket segment, and the fix differs completely depending on which shape is actually present. Cross-reference HEART's Retention dimension directly against [north-star-metric.md](north-star-metric.md) and [aarrr-pirate-metrics.md](aarrr-pirate-metrics.md)'s Retention stage — for most clients these measure the same underlying phenomenon from different angles; if they disagree sharply, that's usually an instrumentation or definitional bug worth resolving before trusting either number. Pick 2–3 HEART dimensions relevant to the specific engagement rather than forcing all five — a branding/positioning engagement probably only needs Happiness and Adoption instrumented; a retention-focused engagement needs Engagement and Retention in depth, with Task Success brought in only if usability specifically seems to be the blocker.

## Watch-outs

- Happiness is the dimension most teams skip because it requires a survey instrument, not just event tracking — but a product can show rising Engagement/Adoption/Retention while satisfaction quietly erodes (users returning out of habit or lock-in, not delight). Don't treat behavioral metrics as a full substitute for asking users directly.
- Aggregate retention numbers (one company-wide "monthly churn rate") hide radically different cohort shapes — always segment the retention curve by signup cohort, and where possible by an early behavioral split, before drawing conclusions.
- N-day retention on a low-frequency product (e.g., a tax-filing app used a few times a year) will look terrible using daily-active-style metrics designed for high-frequency products — match the retention window to the product's natural usage rhythm, not a borrowed default from a different category.
- GSM's discipline (goal → signal → metric, in that order) is easy to skip under deadline pressure, reverting to "let's just track what's easy" — that's exactly the failure mode GSM exists to prevent, and skipping it produces a dashboard full of numbers nobody can tie back to an actual UX goal.

## Related

- [north-star-metric.md](../product-management/north-star-metric.md) — HEART's Retention/Engagement dimensions and an NSM's input metrics frequently measure overlapping behavior; use HEART to check for UX-quality blind spots an NSM's single number won't show.
- [aarrr-pirate-metrics.md](../product-management/aarrr-pirate-metrics.md) — AARRR's Retention stage and HEART's Retention dimension address the same phenomenon from a lifecycle-funnel angle versus a UX-quality angle respectively.
- [experimentation-ab-testing.md](../product-management/experimentation-ab-testing.md) — the metrics defined via GSM are typically the same primary/guardrail metrics used to evaluate an A/B test's result.
