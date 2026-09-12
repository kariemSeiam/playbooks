---
domain: strategy
concept: CRISP-DM & MLOps
source: 'research — Chapman et al., "CRISP-DM 1.0: Step-by-step Data Mining Guide" (SPSS/CRISP-DM consortium, 2000); D. Sculley et al., "Hidden Technical Debt in Machine Learning Systems" (NeurIPS, 2015); Google Cloud, "MLOps: Continuous delivery and automation pipelines in machine learning" (2020)'
tags: [data-science, ml, mlops, process, deployment, modeling]
---

# CRISP-DM & MLOps

CRISP-DM (Cross-Industry Standard Process for Data Mining) and MLOps are two complementary process frameworks a consultant needs to judge whether a client's data science or ML effort is run as a disciplined process or as ad hoc modeling. CRISP-DM, the battle-tested six-phase methodology published in 2000, still underlies most professional data science practice; MLOps is the more recent — and still maturing — discipline of applying DevOps-style automation and lifecycle rigor specifically to the parts of CRISP-DM that involve a live, deployed model that must keep working after launch. CRISP-DM answers "how do we responsibly get from a business question to a validated model"; MLOps answers "how do we keep that model reliable, monitored, and retrainable once it's actually running in production."

## When to use

- A client's data science team produces models that never make it to production, or that degrade silently after launch
- Scoping or reviewing a data science engagement, to check whether business framing and evaluation are getting real time relative to modeling
- Diagnosing "hidden technical debt" in an existing ML system — pipeline, data-dependency, and monitoring gaps that don't show up as visible bugs but compound over time
- Standing up a new ML capability — the natural downstream process once [ai-build-vs-buy.md](ai-build-vs-buy.md) produces an "Evolve" (build) decision
- Post-mortem on a failed or stalled ML project — CRISP-DM's phases are a reliable checklist for finding which phase was skipped or under-invested

## How it works

### CRISP-DM — six phases, iterative not strictly linear

| Phase | Question it answers | Common failure if skipped or rushed |
|---|---|---|
| **1. Business Understanding** | What business problem are we solving, and what does success look like in business terms, not model metrics? | A technically impressive model that doesn't move the metric leadership actually cares about |
| **2. Data Understanding** | What data do we actually have, what's its quality, and does it contain a signal for this question at all? | Modeling begins on data that can't support the use case, discovered only after significant sunk cost |
| **3. Data Preparation** | Cleaning, transforming, and joining data into a modeling-ready form — typically the most time-consuming phase in practice | Underestimating this phase is the most common project-planning error; garbage in, garbage out downstream |
| **4. Modeling** | Selecting and tuning modeling techniques against the prepared data | Often the phase with the least actual project risk, despite getting disproportionate attention |
| **5. Evaluation** | Does the model actually meet the business success criteria from Phase 1, not just a statistical metric? | A model with excellent offline accuracy is shipped without ever being checked against the original business question |
| **6. Deployment** | Getting the model into the process or system where it actually creates value, plus a maintenance and monitoring plan | Models that work perfectly in a notebook and are never operationalized — the single most common way data science fails to create business value |

The process is explicitly iterative and non-linear, much like design thinking's stages — CRISP-DM's own diagram loops back from Evaluation to Business Understanding, and from Deployment back to the top, because deployment and monitoring routinely surface new business questions or reveal that "understanding" needs revisiting once the model meets reality.

### MLOps — the discipline that makes Deployment durable

MLOps extends CRISP-DM's Deployment phase, and the ongoing loop back to Business/Data Understanding, into a continuously operated system — applying DevOps principles (automation, versioning, monitoring, continuous integration and delivery) specifically to the parts of the ML lifecycle unique to ML, not just software: data pipelines, model training, and model behavior in production. Core practices:

- **Data and pipeline versioning** — treating training data and feature pipelines as versioned artifacts, not one-off exports, so a model's exact inputs are reproducible
- **Automated retraining pipelines** — scheduled or trigger-based retraining as data distributions shift, rather than manual, ad hoc model refreshes
- **Model monitoring for drift** — detecting when the live data distribution or model performance diverges from what was validated in Evaluation (data drift, concept drift) — effectively CRISP-DM's Evaluation phase running continuously rather than once
- **CI/CD for models** — automated testing and staged rollout (shadow deployment, canary release) of new model versions, mirroring standard software CI/CD but extended with model-quality gates, not just code correctness
- **Hidden technical debt awareness** — Sculley et al.'s 2015 paper is the foundational warning: ML systems accrue a distinct kind of technical debt beyond normal code debt — entanglement (changing anything changes everything, because model inputs interact non-linearly), correction cascades (fixing one model by bolting a correction model on top of it), data dependencies invisible in code review, and system boundaries that are inherently blurrier than traditional software's

## Example

A bank builds a credit-risk model. **Business Understanding** defines success as reducing default rate without increasing rejection of creditworthy applicants — an explicit tradeoff, not just "maximize accuracy." **Data Understanding** discovers eighteen months of transaction history has quality gaps for a third of applicants. **Data Preparation** consumes the majority of the project timeline reconciling and imputing that history. **Modeling** produces a candidate model. **Evaluation** checks it against the original business tradeoff, not just AUC, and confirms it clears the bar. **Deployment** integrates it into the loan-decision workflow. Six months later, MLOps monitoring flags data drift — applicant demographics have shifted post-launch because a new marketing channel brought in a different customer mix — and the automated retraining pipeline flags the model for review before its predictions silently degrade, catching the issue rather than discovering it a year later in a regulatory audit after default rates have already climbed.

## Applying it for a client

Use CRISP-DM's six phases as a structured audit checklist on any existing or proposed data science engagement — ask, phase by phase, how much time and rigor was actually applied, looking specifically at the two most commonly shortchanged phases: Business Understanding (rushed because it isn't "technical work") and Deployment/monitoring (rushed because the visible modeling work feels done once Evaluation passes). For a client standing up a new ML capability, scope the engagement to include MLOps infrastructure — versioning, monitoring, retraining triggers — as a deliverable from day one, not an afterthought bolted on after a model breaks in production; this is the most common gap between a data-science proof-of-concept and an actually reliable production system. Pair this note's Deployment/monitoring rigor directly with [ai-governance-nist-eu.md](ai-governance-nist-eu.md)'s Measure/Manage functions — for a client in a regulated context, model monitoring is not just an engineering best practice, it's part of the compliance obligation.

## Watch-outs

- Data Preparation reliably takes longer than clients, and sometimes data scientists, plan for — budget and timeline estimates that don't reserve the majority of project time for this phase are optimistic by default
- "The model works" (Modeling/Evaluation) and "the model creates business value in production" (Deployment/MLOps) are different claims — a project can succeed at the former and fail entirely at the latter, and that gap is where most ML investment quietly evaporates
- MLOps tooling and maturity varies enormously by organization — don't assume a client has any of it in place; a first ML deployment for a client with no existing MLOps practice needs that infrastructure built as part of the project, not assumed as ambient capability
- Skipping the iterative loop-back — treating CRISP-DM as a strict one-pass waterfall — causes teams to ship models that technically complete all six phases but don't answer the business question, because nobody looped back to Business Understanding once Data Understanding revealed the original framing was off
- Sculley et al.'s "hidden technical debt" argument means an ML system can look stable and low-risk from the outside while accumulating real fragility (entangled dependencies, correction cascades) that only surfaces as a sudden, hard-to-diagnose failure — periodic technical-debt review of production ML systems is risk management, not optional maintenance

## Related

- [ai-build-vs-buy.md](../strategy/ai-build-vs-buy.md) — CRISP-DM and MLOps are the process discipline that governs execution once a capability has actually earned an "Evolve" (build) decision
- [ai-maturity-models.md](../strategy/ai-maturity-models.md) — an organization's ability to run CRISP-DM/MLOps rigorously is itself a marker of Gartner Operational/Systemic-stage maturity, not something available at the Awareness/Active stages
- [ai-governance-nist-eu.md](../strategy/ai-governance-nist-eu.md) — MLOps monitoring is the operational mechanism that satisfies NIST's Measure/Manage functions on an ongoing basis for any deployed model
