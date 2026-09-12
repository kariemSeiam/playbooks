---
domain: operations
concept: Incident Management — ITIL and SRE
source: research — ITIL 4 (owned by PeopleCert); Google SRE Book, Beyer, Jones, Petoff & Murphy (eds.), Site Reliability Engineering (2016)
tags: [incidents, itil, sre, postmortem, slo, reliability]
---

# Incident Management — ITIL and SRE

Two distinct traditions define how modern organizations handle things going wrong. **ITIL 4** — the IT service management framework whose intellectual property was acquired by PeopleCert (formerly co-owned with the UK Cabinet Office under the AXELOS joint venture, which PeopleCert acquired in 2021) — treats incident management as one of its formally defined practices: a structured process for restoring normal service operation as fast as possible, with minimum business impact. **Google's Site Reliability Engineering (SRE)** discipline, documented in the 2016 book *Site Reliability Engineering: How Google Runs Production Systems* (edited by Betsy Beyer, Chris Jones, Jennifer Petoff, and Niall Richard Murphy), treats reliability as an engineering problem measured in explicit numeric targets, with blameless postmortems as the mechanism for turning every incident into durable improvement. A consultant needs both because they answer different questions well: ITIL answers "how do we consistently triage, escalate, and communicate during an incident," and SRE answers "how do we decide, quantitatively, how reliable we actually need to be, and how do we learn systematically from every failure."

## When to use

- A client's incidents are handled inconsistently — response quality depends entirely on who happens to be on call, with no shared priority scheme or escalation path.
- A client has monitoring and dashboards but no agreed, explicit reliability target, so "how reliable are we" has no concrete answer.
- Postmortems (if they happen at all) turn into blame sessions, and staff have started quietly under-reporting or downplaying incidents as a result.
- A client is choosing how much engineering time to spend on reliability work versus new features, and needs a principled way to make that trade-off rather than an ad hoc argument every sprint.
- Scaling an on-call/support function past the point where informal, tribal-knowledge handling of incidents still works.

## How it works

### ITIL 4's incident management practice

Incident management is one of ITIL 4's 34 defined management practices, built around a small set of precise definitions that a consultant should use exactly, since imprecise use of these terms is one of the most common sources of confused escalation in practice:

| Term | Definition |
|---|---|
| **Incident** | An unplanned interruption to a service, or a reduction in its quality. |
| **Problem** | The underlying cause of one or more incidents. |
| **Known Error** | A problem that has been analyzed but not yet resolved — documented so future incidents caused by it can be matched and resolved faster. |
| **Major incident** | An incident with especially significant business impact, requiring an elevated, faster-moving response process distinct from routine incident handling. |

**Priority** in ITIL is a function of two independent inputs, not a single judgment call: **impact** (how much of the business/how many users are affected) crossed with **urgency** (how quickly the impact will worsen if nothing is done) — the resulting impact-urgency matrix is what determines priority and, from there, response time targets and escalation path.

### SRE's core concepts

| Concept | Definition |
|---|---|
| **SLI (Service Level Indicator)** | A specific, measured metric of service behavior — e.g., request latency, error rate. |
| **SLO (Service Level Objective)** | A target value or range for an SLI over a time window — e.g., "99.9% of requests complete under 300ms over 28 days." |
| **SLA (Service Level Agreement)** | An SLO with consequences attached — typically a contractual or business commitment to a customer, with a penalty if missed. |
| **Error budget** | The inverse of the SLO — if the SLO is 99.9%, the error budget is the remaining 0.1% of allowable failure. It functions as a shared resource: as long as the budget isn't exhausted, the team can ship changes and take risk; once it's exhausted, the team's priority shifts explicitly to reliability work over new features. |

**The four golden signals** — SRE's minimum recommended set of things to monitor on any user-facing system: **latency** (how long requests take), **traffic** (how much demand the system is serving), **errors** (the rate of failed requests), and **saturation** (how "full" the system is relative to its capacity). The claim behind naming exactly these four is that a system instrumented on all four rarely has a serious problem invisible to its own monitoring.

**Blameless postmortems** — a written analysis, produced after every significant incident, that focuses entirely on what happened and why the system and process allowed it to happen, explicitly excluding blame directed at any individual. The premise is that punishing individuals for mistakes suppresses the honest reporting that postmortems depend on to actually find root causes — a team that fears blame will (consciously or not) shade the postmortem toward a version that protects people rather than one that surfaces the truth.

### How the two traditions combine in practice

A mature operations organization typically runs ITIL's structured process (priority matrix, defined escalation paths, known-error tracking) as the *scaffolding* for how an incident is triaged and communicated in real time, while running SRE's quantitative discipline (SLOs, error budgets, golden-signal monitoring, blameless postmortems) as the *substance* of how reliability targets are set and how the organization actually improves after each incident. Neither substitutes for the other: ITIL without SRE's numeric rigor produces well-organized incidents that never quantitatively improve system reliability over time; SRE without ITIL's basic process discipline produces sharp engineering insight that never reliably reaches the right people during an actual incident, especially in an organization not already engineering-native.

## Example

A mid-size e-commerce company suffers a checkout outage. ITIL structure kicks in first: the incident is logged, impact (all customers, revenue-generating checkout flow) crossed with urgency (actively losing revenue every minute) puts it at the highest priority, triggering the major-incident process — a named incident commander, a live status channel, and pre-agreed customer-communication templates, rather than an improvised scramble. SRE discipline determines what happens next: the team checks whether this incident has consumed enough of the checkout service's monthly error budget to warrant halting all new feature deployments until reliability work catches up — it has, so a planned feature release is paused. The four golden signals had already flagged rising latency and saturation on the checkout database twenty minutes before the outage, which the on-call engineer had triaged as low-priority; the blameless postmortem's finding isn't "the engineer made a mistake," but that the alerting threshold for that specific signal was set too permissively — and the fix is a lowered alert threshold, not a performance conversation with the individual.

## Applying it for a client

Before recommending tooling, ask which half is actually missing: a client with chaotic, undocumented ad hoc incident response needs ITIL's basic structure (priority matrix, named roles, a known-error log) before SRE's more sophisticated numeric targets will help them at all. A client with plenty of dashboards but no agreed reliability target, and postmortems (if they happen) that quietly turn into blame sessions, needs SRE's SLO/error-budget discipline and an explicit, protected commitment to blamelessness — this second gap is often cultural, not technical, and the fix is a leadership statement and consistent practice, not a new tool. For any client, push for the four golden signals as a minimum monitoring baseline before recommending a larger observability investment — many clients have dozens of dashboards and none of the four signals actually instrumented cleanly. And make the error-budget concept concrete early: ask what the client currently does when reliability is bad — if the honest answer is "nothing changes, we keep shipping features," there's no real error budget in practice, whatever SLO number is written down.

## Watch-outs

- ITIL process without a genuinely blameless postmortem culture becomes bureaucratic theater — tickets get closed and priorities get assigned, but the organization never actually gets more reliable, because nobody is safe to report the real root cause.
- SRE's rigor (SLOs, error budgets, golden signals) introduced into an organization with no basic incident process discipline first tends to produce excellent analysis after chaotic, poorly communicated incidents — sequence the ITIL scaffolding in first if it's missing.
- An error budget that's tracked but never actually changes behavior when exhausted (features keep shipping regardless) isn't functioning as an error budget — it's a vanity metric; the whole mechanism depends on genuinely pausing feature work when it's spent.
- Blameless postmortems require consistent leadership behavior over time to be trusted — a single instance of an individual being blamed or penalized after an "official" blameless postmortem process will permanently damage the honesty of every postmortem that follows.
- Priority (impact × urgency) is frequently collapsed into a single subjective "how bad does this feel" judgment in practice — insist on scoring both dimensions explicitly, since the two don't always move together (a low-impact issue can be extremely urgent, and vice versa).

## Related

- [iso-22301-bcm.md](../operations/iso-22301-bcm.md) — incident response and major-incident escalation are the operational front end that feeds into, and is informed by, the broader business continuity plan.
- [nist-csf.md](../operations/nist-csf.md) — the Respond and Recover functions are the framework-level equivalent of the practices detailed here.
- [lean-six-sigma.md](../operations/lean-six-sigma.md) — blameless postmortems and DMAIC's root-cause analysis (Analyze phase) share the same underlying discipline: find the real cause, not the convenient one.
- [vendor-risk-management.md](../operations/vendor-risk-management.md) — a vendor's own incident-response maturity (documented SLAs, breach notification commitments) is a standard element of third-party risk due diligence.
