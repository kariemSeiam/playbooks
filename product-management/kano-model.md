---
domain: product-management
concept: Kano Model
source: research — Dr. Noriaki Kano ("Attractive Quality and Must-Be Quality", 1984)
tags: [prioritization, feature-classification, customer-satisfaction, quality]
---

# Kano Model

The Kano Model classifies features by the *shape* of the relationship between how much functionality is present and how satisfied the customer is — not just "important vs. unimportant." Dr. Noriaki Kano, a Japanese quality-management professor, developed it in 1984 for manufacturing quality and it was later adapted widely into product management for feature prioritization. A consultant needs it because a flat priority list can't distinguish a feature that merely prevents anger (fix it or customers leave) from a feature that actively creates delight (build it and customers become advocates) — treating both the same way misallocates a scarce roadmap.

## When to use

- Deciding where to invest scarce roadmap capacity between "must fix" table stakes and genuinely differentiating delighters, when the team's default is to treat every requested feature as equally worth pursuing.
- Auditing a mature product for features that have quietly become table stakes — yesterday's delighter is often today's basic expectation, and the model explicitly predicts this decay.
- Resolving stakeholder disagreement where one person calls a feature "critical" and another calls it "nice to have" — Kano gives both a shared vocabulary and a survey-based way to settle it with data.
- Alongside RICE or MoSCoW (see [prioritization-techniques.md](prioritization-techniques.md)) as an additional lens on the *emotional/satisfaction* dimension those scoring methods don't capture on their own.

## How it works

### Five categories, defined by curve shape

1. **Basic / Must-be (Threshold)** — expected, taken for granted. Presence causes no delight (it's just expected); absence causes strong dissatisfaction. The curve only costs you, never gains you goodwill. Example: a banking app that doesn't crash.
2. **Performance / One-dimensional** — satisfaction scales roughly linearly with how much is delivered; more is better, less is worse, in direct proportion. Most spec-sheet competition happens here. Example: page-load speed, battery life, storage capacity.
3. **Excitement / Attractive (Delighters)** — unexpected; absence causes no dissatisfaction (customers didn't know to expect it), but presence creates disproportionate delight. Example: a surprise free upgrade, or a feature nobody asked for that solves a problem they didn't know was solvable.
4. **Indifferent** — customers don't care either way; investment here is close to wasted regardless of how much stakeholder enthusiasm exists for it.
5. **Reverse** — some customers are actively dissatisfied by *more* of the feature (power users want fewer confirmation dialogs; a segment prefers manual control over automation). A reminder that "more of X is better" can be segment-dependent, not universal.

### The decay prediction

Kano's own key prediction: delighters migrate downward over the product's life. An Attractive feature, once customers experience and come to expect it, becomes a Performance feature, and eventually a Basic expectation as the whole market adopts it (GPS navigation in a taxi app was a delighter around 2010; it's a basic expectation today). This means the model must be re-run periodically — a Kano classification is time-stamped, not permanent.

### The Kano Survey — how to classify a feature

For each candidate feature, ask customers a paired question, each answered on the same 5-point scale:

- **Functional form:** "How would you feel if the product HAD [feature]?"
- **Dysfunctional form:** "How would you feel if the product did NOT have [feature]?"

Scale: (1) I like it that way, (2) I expect it to be that way, (3) I am neutral, (4) I can tolerate it that way, (5) I dislike it that way.

Each functional/dysfunctional answer pair is run through Kano's standard evaluation table:

| Functional \ Dysfunctional | 1. Like | 2. Must-be | 3. Neutral | 4. Live-with | 5. Dislike |
|---|---|---|---|---|---|
| **1. Like** | Q | A | A | A | O |
| **2. Must-be** | R | I | I | I | M |
| **3. Neutral** | R | I | I | I | M |
| **4. Live-with** | R | I | I | I | M |
| **5. Dislike** | R | R | R | R | Q |

(A = Attractive, O = One-dimensional, M = Must-be, I = Indifferent, R = Reverse, Q = Questionable — a contradictory pair, treated as noise, usually a poorly worded question.)

Tally results across the sample; the modal category becomes the feature's classification — but check the full distribution, not just the mode. A feature split roughly evenly between two categories across segments is itself a segmentation finding: different customer types want different things from the same feature.

### Better/Worse coefficients

Rather than forcing a single discrete bucket on a borderline feature, compute:

- **Satisfaction (Better) coefficient** = (A + O) / (A + O + M + I) — how much adding the feature increases satisfaction.
- **Dissatisfaction (Worse) coefficient** = −(O + M) / (A + O + M + I) — how much removing it decreases satisfaction (expressed negative, since it's a cost).

These let you plot a feature on a Better/Worse quadrant chart instead of forcing a discrete label when the classification is genuinely close.

## Example

A food-delivery app tests "real-time rider location on a map." Functional question ("how do you feel if the app showed your rider's live location?") — most respondents answer "I like it" (1). Dysfunctional question ("how do you feel if it did NOT show it?") — most answer "I can live with it" (4). Cross-reference the table: Like(1) × Live-with(4) → **Attractive**. It's a delighter today.

Contrast with "app shows the order total before checkout": Functional = "I expect it" (2), Dysfunctional = "I dislike it" (5) → Must-be(2) × Dislike(5) → **Must-be**. No credit for having it, real punishment for missing it.

Now suppose the live-map survey is re-run 18 months later, after three competitors have all shipped the same feature: it likely reclassifies from Attractive toward One-dimensional, or even Must-be — exactly the decay the model predicts, and the reason to re-survey periodically rather than trust an old classification.

## Applying it for a client

Run the paired functional/dysfunctional survey on a shortlist of 8–15 candidate features (more fatigues respondents), with a sample large enough to trust the modal category — aim for at least 30 responses per feature for a small client base, more for a larger one. Use the output as an input to, not a replacement for, RICE or Weighted Scoring (see [prioritization-techniques.md](prioritization-techniques.md)) — Kano tells you the *shape* of satisfaction, but RICE still needs Reach/Effort/Confidence to sequence work; a Must-be feature with huge effort and small reach may still rank behind a cheap Attractive feature that reaches everyone. For a mature client product, re-run the Basic-category classification every 12–18 months — this is the fastest way to catch a client's silent "quality debt": features they still believe are delighting customers but have quietly become table stakes their competitors already match. Flag any Reverse-category finding immediately — it usually indicates the surveyed sample actually contains two distinct segments with opposite needs and should be split (feed into [segmentation-personas.md](segmentation-personas.md)) rather than averaged into one confused priority call.

## Watch-outs

- Don't confuse "Must-be" with "low priority" — Must-be features are often the *highest*-priority defensive work precisely because they generate no credit but cause outsized damage when missing or broken. Kano's categories describe the shape of impact, not its size.
- A single classification isn't permanent — expect Attractive features to decay toward Performance and then Basic as the market catches up; that's the model's own core prediction, not a measurement error.
- Small sample sizes produce noisy modal categories, especially near a 50/50 split between two categories — treat borderline results as "needs a larger sample or is genuinely segment-dependent," not as settled.
- The paired-question format is easy to botch by asking only the functional half ("would you like feature X?") — without the dysfunctional pairing you get generic enthusiasm for everything and lose the entire discriminating power of the method.

## Related

- [prioritization-techniques.md](../product-management/prioritization-techniques.md) — that note names Kano but doesn't elaborate; use it alongside RICE/MoSCoW, not instead of them.
- [jobs-to-be-done.md](../product-management/jobs-to-be-done.md) — a feature's Kano category often shifts once you know the underlying job; a delighter for one job can be indifferent for another.
- [value-proposition-canvas.md](../marketing/value-proposition-canvas.md) — Gain Creators and Pain Relievers on the VPC map roughly onto Kano's Attractive and Must-be categories respectively.
