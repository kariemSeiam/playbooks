---
domain: strategy
concept: AI Governance — NIST AI RMF & EU AI Act
source: research — NIST, "Artificial Intelligence Risk Management Framework (AI RMF 1.0)," NIST AI 100-1 (2023); European Union, Regulation (EU) 2024/1689 (the "EU AI Act")
tags: [ai, governance, regulation, risk, compliance, nist, eu-ai-act]
---

# AI Governance — NIST AI RMF & EU AI Act

The two most consequential AI governance references a consultant needs today are a voluntary US risk-management framework, the NIST AI RMF, which most organizations — including outside the US — use as a practical governance blueprint, and a binding EU regulation, the AI Act, the first comprehensive risk-tiered legal regime for AI, with extraterritorial reach (it applies to any AI system placed on the EU market or affecting people in the EU, regardless of where the provider is based) and fines larger than GDPR's. A consultant advising on AI adoption needs both: NIST for "how do we actually manage AI risk well," and the EU Act for "what are we legally required to do, and by when."

## When to use
- A client is deploying or procuring AI systems and needs a defensible governance process, not ad hoc review
- Any client with EU customers, EU operations, or an AI system whose output could affect people in the EU, regardless of where the company is headquartered
- A board or audit committee wants assurance that AI risk is managed against a recognized framework, not an internal checklist
- Vendor or procurement due diligence — assessing whether a third-party AI vendor's own governance practices are adequate
- Any client asking "are we compliant" ahead of a product launch, fundraising round, or enterprise sales cycle requiring a security/compliance review

## How it works

### NIST AI Risk Management Framework (AI RMF 1.0, 2023)
Voluntary and framework-agnostic — not tied to any specific regulation — organized around four functions applied iteratively across the AI lifecycle rather than as a one-time linear checklist:

| Function | Focus | Example activities |
|---|---|---|
| **Govern** | Cross-cutting — organizational risk culture, accountability, and policy; applies throughout, to all other functions | Who approves high-risk use cases; how third-party models get vetted before adoption; how resources are allocated to safety testing |
| **Map** | Identify context, stakeholders, system boundaries, and potential harms for a specific AI system | Context-setting: intended use, affected populations, foreseeable misuse |
| **Measure** | Assess and quantify risks using both quantitative and qualitative methods | Bias testing, robustness testing, performance monitoring against defined metrics |
| **Manage** | Allocate resources to the risks identified and measured, on an ongoing basis, as defined by Govern | Incident response, mitigation prioritization, ongoing post-deployment monitoring |

Govern is architecturally distinct: it isn't a discrete phase that finishes before Map begins, it's the cross-cutting governance layer that shapes how the other three are actually carried out throughout the AI system's lifecycle. NIST also publishes a companion "AI RMF Playbook" with suggested actions per subcategory, useful as a working checklist alongside the deliberately abstract core framework document.

### EU AI Act — risk-based tiers and phased dates
The Act classifies AI systems into risk tiers with different obligations:
- **Unacceptable risk (prohibited)** — banned outright: social scoring, subliminal manipulation, untargeted facial-recognition scraping, real-time biometric categorization in most public contexts, emotion inference in workplaces and schools
- **High risk** — permitted but heavily regulated (conformity assessment, technical documentation, human oversight, logging): covers systems in biometrics, critical infrastructure, education, employment, essential services, law enforcement, migration/asylum/border control
- **Limited risk** — transparency obligations only, e.g., disclosing that a user is interacting with an AI system, labeling AI-generated or deepfake content
- **Minimal risk** — no specific obligations; the large majority of current AI applications
- **General-purpose AI (GPAI) models** — a separate obligation track regardless of tier, scaled by whether the model presents "systemic risk" (broadly, the most capable, large-scale foundation models)

**Phased timeline** (dates as of mid-2026; the "Digital Omnibus" proposal has already shifted the original high-risk date once, so treat this as subject to further revision):

| Date | What applies |
|---|---|
| **Feb 2, 2025** | Prohibited-practice bans and AI-literacy obligations (Art. 4) took effect |
| **Aug 2, 2025** | GPAI model obligations, national authority designation, and the penalty framework became applicable; any GPAI model released after this date must comply immediately |
| **Aug 2, 2026** (original) → **Dec 2, 2027** (revised) | High-risk obligations for Annex III use cases (biometrics, critical infrastructure, education, employment, migration, etc.) — deferred under the 2026 Digital Omnibus |
| **Aug 2, 2027** | Final compliance deadline for GPAI models already on the market before Aug 2025 (legacy models) |

**Penalties.** Up to €35 million or 7% of global annual turnover, whichever is higher, for the most serious violations (prohibited practices) — exceeding GDPR's maximum of 4% of turnover, making the EU AI Act the highest-stakes AI-specific compliance exposure most global companies currently face.

## Example

A US-based HR-tech vendor sells an AI resume-screening tool to companies with operations in Germany and France. Even though the vendor has no EU legal entity, its tool falls squarely into the EU AI Act's high-risk tier (employment-related AI systems). Under NIST AI RMF, the vendor's Govern function would define who signs off on the model's use in hiring decisions and how bias testing gets resourced; Map would document the system's context and the populations it affects; Measure would run the actual bias and robustness testing; Manage would define the incident-response and mitigation plan if disparate-impact issues surface post-deployment. Separately, under the EU AI Act, the same vendor must complete conformity assessment, maintain technical documentation, and provide human-oversight mechanisms before the high-risk deadline applies to its EU-facing customers — a distinct legal obligation the NIST work does not by itself satisfy.

## Applying it for a client

Run NIST AI RMF as the practical, ongoing governance operating system regardless of jurisdiction — Govern/Map/Measure/Manage gives a defensible structure even for clients with no EU exposure, and increasingly shows up as the reference framework enterprise customers ask vendors about in security questionnaires. Separately and explicitly, run an EU AI Act applicability check as a distinct legal-exposure question: does the client place any AI system on the EU market, or does its output affect people located in the EU? If yes, classify each system into the Act's risk tiers before anything else — the tier determines the entire compliance burden, and clients regularly underestimate whether their system counts as "high-risk" (HR/employment and biometric use cases are the categories most commonly missed). Treat the phased dates as a compliance calendar to build backward from, and flag the Digital Omnibus revision explicitly — a client planning against the original Aug 2026 high-risk deadline may be over- or under-prioritizing relative to the current Dec 2027 date, and this kind of regulatory timeline is exactly the sort of fact to re-verify before quoting to a client rather than repeat from memory.

## Watch-outs
- NIST AI RMF is voluntary and non-binding — following it is good practice and increasingly an expected baseline, but it does not by itself satisfy any specific legal obligation like the EU AI Act's
- The EU AI Act's territorial reach catches non-EU companies — "we're not based in Europe" is not a defensible reason to skip the applicability assessment if EU users or customers are in scope
- Risk-tier misclassification is the highest-stakes mistake — treating a high-risk system (an AI tool used in hiring decisions) as limited or minimal risk because its output "is just a recommendation" is common and expensive; human-in-the-loop framing doesn't automatically downgrade the tier
- Regulatory dates in this space move — the Digital Omnibus proposal already pushed the original Aug 2026 high-risk deadline to Dec 2027 mid-implementation; always verify current dates against the official EU AI Act implementation timeline rather than treating any date, including the ones in this note, as permanently fixed
- Governance frameworks (NIST) and legal compliance (EU AI Act) are complementary, not substitutes — a client can be fully NIST-aligned and still in violation of specific EU AI Act obligations, and vice versa; don't let a client conflate "we have a responsible-AI framework" with "we are legally compliant in every market we operate in"

## Related
- [ai-maturity-models.md](../strategy/ai-maturity-models.md) — governance maturity separates Gartner's later maturity stages from earlier ones; an organization can't credibly claim high maturity without a governance function
- [ai-build-vs-buy.md](../strategy/ai-build-vs-buy.md) — vendor governance posture (does the vendor's tool already handle NIST/EU AI Act obligations) is a real input into the build-vs-buy decision, not just cost or differentiation
- [crisp-dm-mlops.md](../strategy/crisp-dm-mlops.md) — Measure and Manage (NIST) map onto CRISP-DM's Evaluation and Deployment/monitoring phases for teams actually building models in-house
