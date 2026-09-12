---
domain: product-management
concept: AARRR / Pirate Metrics Funnel
source: sources/product-management/civiconnectors-product-management.pdf.card.md
tags: [aarrr, pirate-metrics, funnel, kpis, retention, revenue]
---

# AARRR / Pirate Metrics Funnel

AARRR (Acquisition, Activation, Retention, Revenue, Referral) — nicknamed "Pirate Metrics" for its acronym — is a framework that maps the entire customer lifecycle into five stages, each with its own goal, feature implications, and measurable KPIs. It matters because it prevents the single most common product-metrics mistake: obsessing over top-of-funnel growth (downloads, signups) while a leaky Retention stage quietly cancels out every acquisition dollar spent.

## When to use

Use AARRR whenever you need to diagnose *where* in the customer journey a product is actually underperforming — "growth is flat" is not a diagnosis, "Activation is fine but Retention drops 60% by week 2" is. Use it both as a feature-planning lens (what should we build for each stage?) and a metrics-instrumentation lens (what should we track for each stage?) — the deck treats these as two passes over the same five stages.

## How it works

Each stage has a **goal**, **features to consider when building for it**, and **metrics to track**.

### 1. Acquisition — "How do users find us?"

**Goal:** Attract visitors and turn them into new users; increase app installations.
**Features to build:** Attractive app icon and name; clear value proposition; App Store Optimization (relevant keywords, compelling visuals/screenshots/videos); user reviews and ratings (encourage satisfied users to leave them); smooth, user-friendly onboarding (quick tutorial, minimize steps to start using the app).
**Metrics:** Traffic (visitors to the site), App downloads / conversion rate, Bounce rate (% leaving after the first page), User sign-ups, Cost per acquisition (cost of acquiring a new user through marketing), Channel effectiveness, Traffic source distribution.

### 2. Activation — "Do users have a great first experience?"

**Goal:** Ensure a positive first experience, converting installs into active users.
**Features to build:** Quick access to core features (minimize navigation barriers); first-time user offers/incentives/promotions (exclusive discounts, rewards for first-timers, promotional campaigns); accessible support/help center and FAQs.
**Metrics:** Onboarding completion (% completing the onboarding flow), Time to value (time until the user experiences the core benefit), User activation rate (% completing a desired action/milestone), Trial-to-paid conversion (% of trial users who make their first purchase), First-time conversion rate (% of first-time users completing a first purchase).

### 3. Retention — "Do users come back?"

**Goal:** Encourage and keep users continuing to use the app over time.
**Features to build:** Personalization (personalized recommendations based on past interactions, special-occasion messages, random rewards, loyalty programs, identifying and fixing drop-off points); push notifications (re-engagement reminders, personalized alerts, promotional banners for new features); feedback loops (surveys to collect user opinions); optimizing speed and responsiveness (minimizing crashes).
**Metrics:** Churn rate (% of users who stop using the app in a period), User retention rate (% who continue using the app), Repeat purchase rate (% making multiple purchases), User renewal rate; **Engagement sub-metrics:** Session length (average duration per session), Session frequency (average sessions per user), Daily active users (DAU), Monthly active users (MAU).

### 4. Revenue — "How do you make money?"

**Goal:** Maximize the revenue generated from existing users.
**Features to build:** In-app purchases via a freemium model (free basic version + premium upgrades); subscription plans (tiered subscriptions, monthly/annual options); loyalty programs (point systems, redeemable rewards).
**Metrics:**

- **ARPU** (Average Revenue Per User) — over a specific time frame
- **CLTV** (Customer Lifetime Value) — ARPU × customer lifetime
- **Customer profitability** — LTV minus CAC (this is where Customer Acquisition Cost re-enters the picture, now netted against lifetime value rather than tracked alone)
- **MRR** (Monthly Recurring Revenue) — the predictable revenue baseline
- **Revenue churn** — revenue lost due to cancellation, downgrading, or non-renewal (distinct from *user* churn in the Retention stage — you can lose revenue from downgrades without losing the user at all)

### 5. Referral — "Do users tell others?"

**Goal:** Encourage satisfied users to refer others to the product.
**Features to build:** Referral program (incentives/rewards/discounts for referrers, two-sided rewards benefiting both referrer and new user); user testimonials (encourage users to share success stories, showcase the positive impact of referrals).
**Metrics:** Referral rate (% of users who actively refer others), Referral conversion rate (% of referred leads who convert into users/customers).
**Output:** word-of-mouth marketing and network effects — the loop that feeds back into Acquisition.

## Example

A subscription meditation app sees downloads climbing every month (Acquisition looks healthy) but revenue is flat. Running the funnel stage by stage: Activation is strong (80% complete onboarding), but Retention shows a 70% churn rate by day 7 — users try it once and vanish before the habit forms, so there's never a chance to reach the Revenue stage where the subscription conversion happens. The fix targets Retention specifically (streak reminders, a "day 3" personalized nudge, fixing an identified drop-off point in the onboarding flow) rather than spending more on Acquisition, which would only fill a funnel that's already leaking at stage 3.

## Applying it for a client

Map a client's actual product against all five stages before recommending *any* feature work — clients (and agencies) default to pitching Acquisition ideas (ads, SEO, a referral program) because they're the most visible and the easiest to sell as a project, but the data usually points to Retention or Activation as the real gap. For a clinic client with a booking app, "Referral" is frequently the highest-leverage, lowest-cost stage to invest in (patients already trust the provider) yet the stage most often left with zero instrumentation — ask specifically whether referral rate is even being measured before recommending new acquisition spend. For a startup, insist the client can name at least one metric per stage before you build anything — a roadmap built to please "growth" in the abstract, without stage-level metrics to check against, cannot be evaluated after launch.

## Watch-outs

- Revenue churn and user churn are not the same number and shouldn't be tracked as if they were — a plan can retain 95% of users while losing 20% of revenue to downgrades, and only tracking user churn would hide that.
- CAC only becomes meaningful paired with CLTV (as "customer profitability = LTV − CAC") — a low CAC on customers who churn in a month can still be a losing business.
- Don't build Retention features (loyalty points, gamification) before Activation is solid — rewarding a habit that hasn't formed yet (weak time-to-value) doesn't fix why users aren't coming back.
- The five stages are sequential for diagnosis but not strictly sequential for feature investment — Referral features can and should be built early if the product is inherently word-of-mouth-driven; don't treat the order as a rigid roadmap.

## Related

- [segmentation-personas.md](../product-management/segmentation-personas.md)
- [prioritization-techniques.md](../product-management/prioritization-techniques.md)
- [business-model-canvas.md](../product-management/business-model-canvas.md)
