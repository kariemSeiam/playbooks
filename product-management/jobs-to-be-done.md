---
domain: product-management
concept: Jobs-to-be-Done (JTBD)
source: research — Clayton Christensen ("Competing Against Luck", 2016) + Tony Ulwick (Outcome-Driven Innovation, "What Customers Want", 2005)
tags: [customer-research, segmentation, innovation, discovery]
---

# Jobs-to-be-Done (JTBD)

Jobs-to-be-Done reframes what a customer is doing when they buy something: they aren't buying a product, they're "hiring" it to make progress on a specific job, in a specific circumstance. Clayton Christensen built the narrative version of this theory (illustrated by his famous milkshake study) to explain why demographic segmentation routinely fails to predict purchase behavior; Tony Ulwick's earlier and parallel Outcome-Driven Innovation (ODI) work operationalizes the same idea into surveyable, scorable "desired outcome statements." A consultant needs both halves — Christensen's version to discover the real job through interviews, Ulwick's version to quantify which parts of that job are underserved enough to be worth building for.

## When to use
- Demographic or firmographic segmentation isn't explaining why customers actually choose (or abandon) a product — the "who" data is fine but doesn't predict behavior.
- Early-stage innovation and new-product ideation, to find underserved or overserved jobs rather than copy a competitor's feature list.
- Repositioning or messaging work, especially when the product's real competitive set includes non-obvious substitutes (a job's true competitor may be a spreadsheet, not another SaaS tool).
- Churn analysis — understanding what job a customer "fired" your product for and hired an alternative (including doing nothing) to do instead.
- Feeding a prioritization process (RICE, Weighted Scoring) with a customer-value input more rigorous than a gut-feel importance score.

## How it works

### The job statement
Standard structure: **"When** [situation/circumstance]**, I want to** [motivation/action]**, so I can** [expected outcome/progress].** The emphasis on circumstance rather than persona is deliberate — the same person hires different products for the same category of task depending on context (a commuter buys a milkshake very differently from a parent buying one for a child's Saturday treat).

### Three dimensions of a job
A job is rarely purely functional — most jobs carry all three, and missing the social/emotional ones is the most common reason a functionally-correct product still underperforms:
- **Functional** — the practical task to accomplish.
- **Social** — how the customer wants to be perceived by others while getting the job done.
- **Emotional** — how the customer wants to feel while doing it (or having done it).

### The four forces of progress
A customer switches to a new solution only when the forces pushing them toward change outweigh the forces holding them back:
- **Push** of the current situation — dissatisfaction with the status quo.
- **Pull** of the new solution — attraction to what the new thing promises.
- **Anxiety** about the new solution — fear it won't work, will be hard to learn, or carries risk.
- **Habit/Allegiance** to the current situation — inertia, sunk cost, familiarity.

Switch happens only when (Push + Pull) > (Anxiety + Habit). Teams routinely over-invest in Pull (better features) and ignore Anxiety and Habit, which are frequently the actual blockers.

### Christensen's field process (qualitative — for discovering the job)
1. Identify a recent "hiring" moment — someone who actually bought, switched, or adopted recently.
2. Run a **switch interview**: reconstruct the timeline from first passive thought, to active looking, to deciding, to first use — anchored to a real, specific event rather than hypothetical preferences.
3. Map the four forces at play at each point on that timeline.
4. Extract the job statement and the real competitive set (which may include non-consumption — "did nothing" is often the true incumbent).

### Ulwick's Outcome-Driven Innovation (ODI — quantitative, for prioritizing within the job)
- **Desired Outcome Statement format:** "Minimize/increase the [metric] of [action] [object] [contextual clarifier]" — e.g., "Minimize the time it takes to reconcile a payment." Solution-free by design; it says nothing about how.
- **Job Map** — every core functional job passes through 8 universal steps: Define, Locate, Prepare, Confirm, Execute, Monitor, Modify, Conclude. Walking a job through this map systematically generates a comprehensive set of desired outcome statements instead of relying on whatever the team happens to think of.
- **Opportunity Score** — survey a large sample on each outcome statement's Importance (1–10) and current Satisfaction (1–10), then compute:

  `Opportunity Score = Importance + max(Importance − Satisfaction, 0)`

  High importance + low satisfaction → high opportunity score → underserved, prioritize. High importance + high satisfaction → table stakes, defend but don't over-invest further. Low importance → deprioritize regardless of satisfaction (overserved or irrelevant).

### Which to use when
Use Christensen's narrative interviews first, when the job itself isn't yet understood — they generate the hypothesis. Use Ulwick's ODI survey second, once you have candidate outcome statements to validate and rank at scale — this mirrors the interview-then-survey sequencing described in [mvp-customer-validation.md](mvp-customer-validation.md): one tool builds the hypothesis, the other measures it.

## Example

**Christensen's milkshake study:** a fast-food chain wanted to sell more milkshakes and initially tried demographic segmentation (surveying "milkshake lovers" on flavor and thickness preferences) with no useful result. Switch interviews revealed roughly 40% of milkshakes were sold before 7am to solo commuters. The job wasn't "dessert" — it was "give me something filling, one-handed, and non-messy to make a boring commute more interesting until lunch." The real competitive set was bananas, bagels, and boredom, not other milkshake brands. The fix: thicken the shake so it lasts the whole commute, move the dispenser toward the front for a fast card-swipe purchase, add small fruit chunks for occasional surprise — none of which came from a flavor-preference survey.

**ODI worked example:** a fintech's ops team scores two desired outcome statements from a customer survey. "Minimize the time it takes to reconcile a payment": Importance = 9, Satisfaction = 4 → Opportunity Score = 9 + (9−4) = **14** (high-opportunity, prioritize). "Minimize the number of clicks to export a report": Importance = 9, Satisfaction = 8.5 → Opportunity Score = 9 + 0.5 = **9.5** (already well-served; further investment here has diminishing returns).

## Applying it for a client

Run 8–12 switch interviews with customers who recently bought or switched, using the timeline method (first thought → passive looking → active looking → deciding → first use) — this produces far richer signal than a generic persona interview because it's anchored to one real event rather than a general opinion. For a data-poor client, lean on Christensen's narrative version to generate hypotheses fast and cheaply. For a client with an existing large user base, layer Ulwick's ODI survey on top to quantify Opportunity Scores across a systematically-generated set of outcome statements (via the Job Map's 8 steps), producing a ranked, defensible input to the backlog rather than a stand-alone research deliverable. Reframe the client's positioning brief around the job statement instead of a persona bio — this step alone often reveals the client's assumed competitive set is too narrow (or too broad).

## Watch-outs

- JTBD doesn't replace segmentation — it complements [segmentation-personas.md](segmentation-personas.md); you still need to know who is likely to have a given job at scale, JTBD explains why they'd hire something for it.
- Skipping the four-forces mapping and writing only a job statement causes teams to over-invest in Pull (better features) while ignoring Anxiety and Habit, which are frequently the actual adoption blocker.
- ODI's Opportunity Score is only as good as the clarity of the outcome statements and the sample size behind them — vague statements ("make it easier to use") produce meaningless scores; every statement must be specific, measurable, and solution-free.
- Don't confuse the job with the current solution category — asking "what job does a drill do" must produce "make a hole," not "own a drill." Skipping that reframe just relabels existing feature requests as "jobs" without gaining anything.

## Related

- [segmentation-personas.md](../product-management/segmentation-personas.md) — JTBD reframes segmentation around outcome/job rather than demographics; use the two together, not as substitutes.
- [continuous-discovery.md](../product-management/continuous-discovery.md) — the Opportunity Solution Tree's "Opportunities" layer is frequently seeded directly from JTBD switch interviews.
- [prioritization-techniques.md](../product-management/prioritization-techniques.md) — Ulwick's Opportunity Score is a direct, more rigorous input to RICE or Weighted Scoring's customer-value criterion.
- [value-proposition-canvas.md](../marketing/value-proposition-canvas.md) — the VPC's "Jobs" field is a lightweight version of full JTBD; this note is the deeper mechanism behind that field.
