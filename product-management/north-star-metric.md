---
domain: product-management
concept: North Star Metric
source: research — Sean Ellis ("Hacking Growth", 2017) / Amplitude's North Star Playbook
tags: [metrics, growth, alignment, product-strategy]
---

# North Star Metric

A North Star Metric (NSM) is the single metric that best captures the core value a product delivers to customers — chosen so that it also leads (rather than lags) revenue, and can rally an entire company around one number instead of every team optimizing its own siloed metric. The term comes out of the growth-hacking circles Sean Ellis helped define, and was later systematized into a repeatable framework by Amplitude, whose "North Star Playbook" is the closest thing the industry has to a standard operating manual for choosing and operationalizing one. A consultant needs it because "growth is our priority" is not a plan — an NSM is the artifact that turns that intention into one number every team's roadmap and OKRs can be checked against.

## When to use

- Teams are optimizing different, sometimes conflicting metrics (growth chases signups, engineering chases uptime, sales chases MRR) and leadership needs one number that ties them together.
- A company has passed initial product-market fit and needs a durable growth metric beyond vanity counts like downloads or pageviews.
- Diagnosing whether shipped features are actually compounding into durable value — an NSM that stays flat despite a busy release calendar is a sharper signal than "we shipped a lot this quarter."
- Setting top-level company OKRs (see [okrs.md](okrs.md)) — the NSM is the natural candidate for the company-level Key Result everything else ladders up to.
- Building a board update or fundraising narrative that needs one defensible, trackable growth number instead of a grab-bag of metrics chosen to look good this quarter.

## How it works

### Criteria for a good NSM

A metric earns "North Star" status only if it passes all of these:

| Criterion | Test |
|---|---|
| Expresses value | Does the number go up specifically when customers get more of the value the product promises? |
| Leading indicator of revenue | Does it move before revenue does, not just alongside it? |
| Actionable | Can teams point to concrete initiatives that would move it, or is it too abstract to act on? |
| Understandable | Can anyone in the company explain what it means in one sentence? |
| Measurable and trackable | Is the underlying event data already (or cheaply) instrumented? |

Revenue itself almost never qualifies — it's a lagging output of value delivered, not the delivery of value itself. Vanity metrics (downloads, registered accounts, pageviews) usually fail the "expresses value" test — they measure exposure to the product, not use of it.

### The metric tree: NSM + input metrics

An NSM sits at the top of a tree with 3–5 **input metrics** feeding it — the specific, ownable levers that, moved together, move the NSM. Each input metric gets its own owner and its own set of initiatives/experiments. Input metrics typically split across four dimensions:

- **Breadth** — how many customers engage in the value-driving behavior
- **Depth** — how much of the behavior each customer does
- **Frequency** — how often they do it
- **Efficiency** — how much effort/friction it takes them to do it

### Process to derive an NSM

1. Write down the product's core value proposition / "aha moment" in one sentence.
2. List every candidate metric that plausibly reflects delivered value.
3. Score each candidate against the criteria table above; discard anything that fails "expresses value" or "actionable."
4. Pick one. Break it into 3–5 input metrics across the breadth/depth/frequency/efficiency dimensions.
5. Assign an owner (team or individual) per input metric.
6. Set a target and a review cadence — weekly or biweekly for an NSM review meeting, not quarterly; the whole point is a leading indicator you can act on inside the current cycle.

### Named examples worth knowing

| Company | North Star Metric |
|---|---|
| Slack | Number of messages sent within a team |
| Airbnb | Nights booked |
| Spotify | Time spent listening |
| HubSpot | Weekly active teams |
| LinkedIn | Sessions |
| Amplitude (their own product) | Weekly learning users |

## Example

A B2B project-management SaaS chooses the NSM **"Weekly Active Projects with 3+ collaborators"** — it passes the criteria table (a project only counts if it's actually being used collaboratively, which is the product's real value, and it correlates with seat expansion months before renewal). Input metrics: (1) new projects created per week (breadth), (2) % of new projects that reach 3+ collaborators within 7 days (depth), (3) % of active projects still edited in week 4 (frequency/durability), (4) invites sent per project (a proxy lever for depth). Baseline: 1,200 qualifying projects/week. The growth team owns invites-per-project and runs an experiment adding an in-app "invite your team" nudge at project creation, raising invites sent per project from 1.4 to 2.1 over one quarter; qualifying projects rise to 1,540/week — a number the whole company reviews weekly, not just the growth team.

## Applying it for a client

Run the NSM derivation as a facilitated workshop with the client's leadership team, not a solo consulting deliverable — the "one sentence value proposition" step routinely surfaces disagreement about what the product actually does for customers, and that disagreement needs to be resolved before a metric can be chosen credibly. Once chosen, insist the NSM becomes the anchor for the next OKR cycle's top-level Key Result (see [okrs.md](okrs.md)) rather than a metric that lives only on a dashboard nobody's roadmap references. For an early-stage client with thin data, be honest that the input-metric breakdown may need to change every quarter or two as understanding of the product's actual value driver sharpens — don't present the first NSM as permanent.

## Watch-outs

- A single metric invites gaming — a client team that over-indexes on "time spent" alone can drift toward engagement-bait rather than genuine value; pair the NSM with guardrail/counter-metrics (satisfaction, complaint rate) that would flag this.
- An NSM chosen once at launch and never revisited becomes misleading after a pivot or business-model change — the metric needs to evolve with the product, not outlive its relevance.
- Picking a metric too broad or abstract to tie to any specific feature or experiment makes it decorative rather than operational — if no team can name an initiative that would move it, it fails the "actionable" test and shouldn't have passed selection.
- An aggregate NSM can rise company-wide while collapsing for a specific, important segment (e.g., enterprise accounts) — segment the NSM regularly, don't trust the topline number alone.
- Don't let the NSM replace all other metrics — it's a rallying number, not a full measurement system; see [product-analytics-heart.md](product-analytics-heart.md) for the UX-quality dimensions it won't capture on its own.

## Related

- [aarrr-pirate-metrics.md](../product-management/aarrr-pirate-metrics.md) — AARRR is the full lifecycle funnel; the NSM is usually a single rollup drawn from its Activation or Retention stage.
- [okrs.md](../product-management/okrs.md) — the NSM commonly becomes the top-level Objective's Key Result.
- [product-analytics-heart.md](../product-management/product-analytics-heart.md) — HEART covers the UX-quality dimensions a single NSM won't surface on its own.
