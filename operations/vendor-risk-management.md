---
domain: operations
concept: Vendor and Third-Party Risk Management
source: research — Shared Assessments Program, Standardized Information Gathering (SIG) Questionnaire
tags: [vendor, risk, third-party, assessment, supply-chain]
---

# Vendor and Third-Party Risk Management

Third-Party Risk Management (TPRM) is the discipline of assessing and monitoring the risk a vendor, supplier, or partner introduces into an organization — because an organization's own security, quality, and continuity controls are only as strong as the weakest vendor it depends on. The Shared Assessments Program is the industry body behind the most widely used standardized tool for this work, the SIG (Standardized Information Gathering) Questionnaire, and also runs the CTPRP (Certified Third-Party Risk Professional) credential for practitioners in the field. A consultant needs this framework because vendor risk is one of the most consistently under-resourced areas in growing organizations — a client can have excellent internal security and quality controls and still suffer a breach, an outage, or a compliance failure caused entirely by a vendor nobody had properly assessed.

## When to use

- A client is onboarding a new vendor that will touch sensitive data, critical infrastructure, or a regulated process (payments, health data, PII).
- A client's own customers, auditors, or regulators are now asking the client to demonstrate a formal vendor risk management program, not just informal trust in existing suppliers.
- A client has never tiered its vendors by actual risk, and is either applying the same light-touch trust to a critical vendor as to a low-risk one, or drowning every vendor relationship in unnecessary questionnaire overhead.
- Diagnosing an incident or near-miss that traced back to a vendor — the review should surface whether onboarding due diligence would have caught the risk, and whether ongoing monitoring should have.
- Preparing a client for its own SOC 2, ISO 27001, or HIPAA compliance work, since all three explicitly require a vendor/third-party risk management component.

## How it works

### Risk tiering comes first

Not every vendor deserves the same scrutiny, and the single most common TPRM mistake is skipping tiering and applying one uniform process to every vendor regardless of actual risk. Vendors are typically tiered by a combination of: what data or systems they can access, how critical their service is to the client's own operations, and how replaceable they are on short notice. A payroll processor handling employee bank details and a stationery supplier are not the same risk category, and treating them identically either wastes effort on the low-risk vendor or under-scrutinizes the high-risk one.

### The SIG questionnaire — matched to tier

The Shared Assessments SIG questionnaire is the standardized instrument used to gather a vendor's own self-reported control information, available at different depths so the assessment effort matches the vendor's risk tier:

| Version | Approximate scope | Fits |
|---|---|---|
| **SIG Lite** | ~126 questions, a high-level overview across major control domains | Lower-risk vendors, or an initial screen before deciding whether deeper assessment is warranted |
| **SIG Core** | ~855 questions, full-depth coverage across all control domains | Critical, high-risk vendors — those with broad access to sensitive data or systems central to the client's operations |

(Both figures are approximate and change slightly release to release as Shared Assessments updates the current version — treat them as order-of-magnitude, not exact counts, when advising a client on effort/time budgeting.) The SIG's questions are explicitly mapped to major external frameworks — including NIST, ISO 27002, GDPR, and HIPAA — so a vendor's SIG responses can be cross-referenced against whichever compliance frameworks the client itself needs to satisfy, rather than requiring a separate custom questionnaire per framework.

### The TPRM lifecycle

1. **Tier the vendor** — classify risk based on data access, criticality, and replaceability, before deciding assessment depth.
2. **Due diligence** — collect and review evidence: a SIG questionnaire matched to tier, plus existing third-party attestations the vendor already holds (a SOC 2 report, an ISO 27001 certificate) rather than duplicating work those already cover.
3. **Contract and legal terms** — formalize security, privacy, and continuity obligations in the contract itself, including a BAA where PHI is involved (see [hipaa-hitrust.md](hipaa-hitrust.md)), and defined SLAs and breach-notification timelines.
4. **Ongoing monitoring** — risk doesn't freeze at onboarding; higher-tier vendors need periodic reassessment, monitoring for security incidents or adverse news, and a defined cadence for refreshing due-diligence evidence (e.g., annually for critical vendors).
5. **Offboarding** — when a vendor relationship ends, formally revoke access and confirm data return or destruction — an offboarded vendor that still has live system access or unreturned data is a live, frequently overlooked risk.

### Why this matters even for vendors that seem "just" operational

A vendor doesn't need to be an obvious "security vendor" to carry real third-party risk — a customer-support ticketing tool, a payroll processor, an email marketing platform, or a logistics partner can each expose sensitive data or create an operational dependency the client hasn't mapped. The most damaging vendor incidents historically have come through vendors the affected organization considered peripheral — a physical-facilities or HVAC-services vendor with network access being a widely cited industry example — precisely because peripheral-seeming vendors are the ones most likely to be onboarded with little or no due diligence at all.

## Example

A mid-size healthtech client tiers its roughly 40 active vendors for the first time: three are classified critical (its cloud hosting provider, its EHR/patient-records platform, its payment processor), eight are classified moderate (analytics, support ticketing, email), and the rest are low-risk (office supplies, a design agency with no data access). The three critical vendors each get a SIG Core assessment plus a request for their own SOC 2 or ISO 27001 report as corroborating evidence — the cloud host already holds ISO 27001, which the client accepts as satisfying most of the SIG Core questions on physical and infrastructure security rather than re-litigating them. The eight moderate vendors get SIG Lite plus a signed data-processing addendum. The review also surfaces that the support-ticketing vendor — categorized informally as "just a tool," never previously assessed — actually receives patient messages containing PHI through support tickets, requiring a retroactive BAA that hadn't existed until the tiering exercise forced the question.

## Applying it for a client

Always tier before assessing — walking straight into questionnaires without first classifying vendors by actual risk either burns time on low-risk vendors or, worse, misses that a "just a tool" vendor is quietly high-risk, as in the example above. Reuse a vendor's existing attestations (SOC 2 report, ISO 27001 certificate) as evidence wherever available rather than re-collecting the same information through a fresh questionnaire — this respects both parties' time and is standard, accepted practice in mature TPRM programs. Build ongoing monitoring into the contract from day one rather than treating due diligence as a one-time onboarding gate — a vendor that was low-risk at onboarding can become high-risk later (a data breach, an ownership change, expanded system access), and a program with no reassessment cadence will miss that drift entirely. And always explicitly include offboarding in the program — an ended vendor relationship with lingering system access or unconfirmed data destruction is a common, easily overlooked residual risk.

## Watch-outs

- Questionnaire fatigue is real on both sides — sending a full SIG Core to every vendor regardless of tier trains vendors to give perfunctory answers and burns internal review capacity that should go to the vendors that actually warrant it.
- A completed questionnaire that's filed and never followed up on is "check-the-box" risk management, not real due diligence — review responses critically, follow up on gaps, and don't treat a returned form as equivalent to a verified control.
- Peripheral-seeming vendors (support tools, marketing platforms, facilities services) are exactly the ones most likely to be onboarded with zero assessment — deliberately audit the client's full vendor list for ones that were never formally tiered at all, not just the obviously data-heavy ones.
- Reusing a vendor's SOC 2 or ISO 27001 report as evidence is efficient, but check the report's actual scope and date — a report scoped to a different product line, or more than a year stale, may not actually cover what the client needs assured.
- Offboarding is the step most TPRM programs skip entirely — a formal, checked-off access-revocation and data-return step should be as mandatory as the onboarding due diligence was.

## Related

- [soc2-compliance.md](../operations/soc2-compliance.md) — a vendor's SOC 2 report is one of the most commonly accepted pieces of due-diligence evidence in a SIG-based assessment.
- [iso-27001-isms.md](../operations/iso-27001-isms.md) — likewise, a vendor's ISO 27001 certificate and Statement of Applicability can substitute for re-collecting the equivalent SIG questions directly.
- [hipaa-hitrust.md](../operations/hipaa-hitrust.md) — BAAs and PHI-flow mapping are the healthcare-specific legal layer of vendor risk management covered there.
- [nist-csf.md](../operations/nist-csf.md) — the SIG questionnaire's questions are explicitly mapped against NIST's control language, among other frameworks.
- [procurement-and-logistics.md](../operations/procurement-and-logistics.md) — vendor tiering and diversification here parallel the supplier-diversification and vendor-development strategies covered there, applied specifically to risk rather than cost and continuity.
