---
domain: product-management
concept: Experimentation & A/B Testing
source: research — Ronny Kohavi, Diane Tang, Ya Xu, "Trustworthy Online Controlled Experiments" (2020); industry practice (Optimizely, LaunchDarkly, Statsig)
tags: [experimentation, feature-flags, data-driven, validation]
---

# Experimentation & A/B Testing

Experimentation is the practice of using controlled rollouts — feature flags, A/B tests, and staged releases — as the actual decision mechanism for whether a change ships, instead of shipping based on opinion or the highest-paid-person's-opinion (HiPPO). An A/B test (an online controlled experiment) randomly assigns users to a control (existing experience) or treatment (new experience) group and measures whether a chosen metric differs by more than chance would predict. A consultant needs the mechanics, not just the concept — most of the value (and most of the failure modes) live in the statistical details of how a test is designed, run, and read, which is exactly what Kohavi's book, drawn from running experiments at scale at Microsoft, Airbnb, and elsewhere, documents in depth.

## When to use

- A change is expected to affect a measurable metric and the cost of being wrong (in either direction) justifies the setup overhead of a properly randomized test, rather than a full unguarded rollout.
- Rolling out a risky change safely — feature flags let code ship to production dark, then ramp exposure gradually, catching regressions on a small population before they hit everyone.
- Resolving genuine stakeholder disagreement about which of two designs or flows performs better, when a decision would otherwise be settled by opinion or seniority.
- Validating an Assumption Test from an Opportunity Solution Tree (see [continuous-discovery.md](continuous-discovery.md)) at a scale beyond what a small qualitative test can tell you.
- Auditing whether an already-shipped feature is actually working — many features ship without ever being tested, and post-hoc measurement (if instrumented) is the only way to know whether they helped, hurt, or did nothing.

## How it works

### Feature flags — the delivery mechanism underneath most experimentation

A feature flag decouples *deploy* (code is in production) from *release* (code is exposed to users) — code can be merged and deployed dark, then exposed gradually or to specific segments with no new deployment.

- **Release flags** — temporary, removed once fully rolled out; used for progressive delivery/canarying.
- **Experiment flags** — drive an A/B test's variant assignment; typically removed once the test concludes and a winner ships.
- **Ops flags** — kill-switches for operational control (e.g., disabling a feature under load).
- **Permission flags** — long-lived, gate a feature by plan tier or user segment; these are the mechanism PLG pricing gates run on (see [product-led-growth.md](product-led-growth.md)).

**Progressive rollout / canary pattern:** ramp a change through increasing exposure tiers (internal dogfood → 1% → 5% → 25% → 100%), watching guardrail metrics (error rate, latency, crash rate) at each tier before increasing exposure — this catches severe regressions cheaply, on a small blast radius, well before an A/B test's statistical result would even be ready.

### A/B test mechanics — the statistical core

1. **Hypothesis** — state it in falsifiable form before running anything: "Changing X will increase/decrease [metric] by [some effect], because [reasoning]." A test without a pre-stated hypothesis invites post-hoc metric-shopping.
2. **Randomization unit** — decide what gets randomly assigned (usually the user, sometimes session or device); it must stay consistent for the test's duration and be independent between units — a real risk in social/network products, where one user's assignment can influence another's experience.
3. **Primary metric** — one pre-declared metric the test lives or dies by; guardrail metrics are also declared upfront to catch unintended harm (e.g., an engagement-boosting change that tanks retention or spikes support tickets).
4. **Sample size / power calculation** — done *before* the test starts, based on the minimum effect size worth detecting, the metric's baseline variance, the desired statistical power (industry convention: 80% — an 80% chance of detecting a true effect of the specified size if it exists), and the significance threshold (industry convention: α = 0.05, a 5% false-positive rate). Skipping this is how teams end tests too early on noise.
5. **Run duration** — long enough to capture at least one full business cycle (commonly a full week minimum, to average out day-of-week effects) and to reach the pre-calculated sample size — not "until the numbers look good," which is p-hacking.
6. **Statistical vs. practical significance** — a result can be statistically significant (unlikely due to chance, p < 0.05) yet practically trivial (a 0.1% lift not worth the added complexity to maintain). Always report effect size and confidence interval, not just whether p crossed 0.05.
7. **Novelty and primacy effects** — a new design can win purely because it's new (novelty effect, fades over days/weeks) or lose purely because existing users resist change (primacy/change-aversion effect, also fades). Run tests long enough, and where possible check whether the effect persists for both new and returning users, to separate a genuine lift from a temporary reaction to change.

### Pitfalls Kohavi's research specifically documents

- **Sample Ratio Mismatch (SRM)** — if you assigned 50/50 but observe, say, 48/52 in the actual data, something is broken in randomization or logging, and the test's results aren't trustworthy until the mismatch is root-caused. Check this before reading any metric result.
- **Peeking** — repeatedly checking a test's results before it reaches its planned sample size or duration and stopping early on a favorable-looking result inflates the false-positive rate substantially. Use a pre-registered stopping rule or a sequential-testing method designed for early stopping, not ad hoc peeking.
- **Twyman's Law** — any result that looks unusually large or good is more likely due to a measurement or instrumentation error than a genuine effect. Large, surprising wins deserve extra scrutiny before being trusted, not extra celebration.

## Example

A checkout-page test: hypothesis — "Moving the coupon-code field from default-visible to behind a 'have a promo code?' link will increase completed-purchase rate by reducing users who abandon checkout to go find a coupon online." Primary metric: completed-purchase rate. Guardrail metrics: revenue per session (in case coupon usage was driving larger basket sizes) and support tickets mentioning "coupon." Baseline completed-purchase rate is 4.2%; detecting a 5% relative lift (4.2% → 4.41%) at 80% power and 95% significance requires roughly 380,000 users per arm, so the test runs three weeks to span both weekday and weekend cycles. Result: treatment shows 4.55% (an 8.3% relative lift, p = 0.01, statistically significant), and the revenue-per-session guardrail is flat — no cannibalization from lost coupon usage — so the team ships to 100%.

Contrast with what not to do: a parallel team peeks at day 2 of a similar test, sees treatment ahead by an early, noisy 15%, and ships immediately. By day 10, the gap had actually closed to a non-significant difference — the "win" was peeking noise, not a real effect.

## Applying it for a client

Before recommending an experimentation program, check the client actually has the instrumentation (event tracking, a flagging system, a stats pipeline) to run a trustworthy test at all — recommending A/B testing to a client with no reliable analytics sets them up to make decisions on noise dressed as data. For an early client with low traffic, be honest that many changes simply won't reach statistical significance in a reasonable timeframe; recommend qualitative validation ([continuous-discovery.md](continuous-discovery.md), [mvp-customer-validation.md](mvp-customer-validation.md)) or a staged rollout with guardrail-metric monitoring instead of forcing an underpowered A/B test that produces an inconclusive, misleading result. Insist on a pre-registered hypothesis, primary metric, and sample-size calculation *in writing* before any test launches — this single practice is the best defense against a stakeholder reinterpreting an inconclusive or negative result as a win after the fact by picking a different metric post-hoc. Recommend feature flags for risk management even outside a formal A/B test — a progressive canary rollout is worth suggesting to every client shipping a meaningful change, independent of whether they have the traffic to run statistically valid experiments.

## Watch-outs

- **Metric-shopping / HARKing** (Hypothesizing After Results are Known) — running a test, finding the primary metric didn't move, then combing through a dozen secondary metrics until one shows "significance," is how false positives get shipped as real wins. The primary metric must be declared before the test starts and honored afterward.
- **Underpowered tests** — running for a fixed duration regardless of traffic, rather than the sample size the effect actually requires, frequently produces an inconclusive result misread as "there is no effect" (absence of evidence isn't evidence of absence).
- **Peeking and early stopping** on favorable interim results, as in the worked example above, is the single most common way teams fool themselves. Set the stopping rule before the test starts and stick to it.
- **Twyman's Law, again** — a client excitedly reporting a huge, surprising lift from a small change should trigger instrumentation-bug suspicion before celebration; verify Sample Ratio Mismatch and event-logging correctness first.
- A/B testing answers "did this specific change work," not "what should we build" — it's a validation tool downstream of discovery ([continuous-discovery.md](continuous-discovery.md)), not a substitute for generating good hypotheses in the first place.

## Related

- [continuous-discovery.md](../product-management/continuous-discovery.md) — Assumption Tests at the Opportunity Solution Tree's leaves are frequently executed as the A/B tests and feature-flagged rollouts described here.
- [product-analytics-heart.md](../product-management/product-analytics-heart.md) — the metrics instrumented via HEART/GSM are typically the same primary and guardrail metrics an experimentation program measures against.
- [product-led-growth.md](../product-management/product-led-growth.md) — permission-style feature flags are the mechanism PLG pricing gates (free vs. paid feature access) run on operationally.
