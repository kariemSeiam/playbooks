---
domain: operations
concept: ISO 27001 Information Security Management System
source: research — ISO/IEC 27001:2022, International Organization for Standardization / International Electrotechnical Commission
tags: [security, isms, iso, certification, controls, risk]
---

# ISO 27001 Information Security Management System

ISO/IEC 27001 is the international standard for an Information Security Management System (ISMS) — a documented, risk-driven set of processes an organization runs to protect the confidentiality, integrity, and availability of its information assets, and to prove, through external audit, that those processes are actually followed rather than just written down. First published in 2005 and most recently revised as ISO/IEC 27001:2022, it is the standard most enterprise buyers, investors, and regulators reach for as shorthand evidence that a vendor takes information security seriously. A consultant needs this framework because it has become close to a default trust signal in B2B software and any data-handling business — a SaaS company without it (or without a credible plan toward it) is increasingly excluded from enterprise procurement before a conversation about the product even starts.

## When to use

- A client's prospective enterprise customers require ISO 27001 certification (or evidence of an active path toward it) as a condition of the contract.
- A SaaS, fintech, or telemedicine client handles sensitive customer data and needs a structured, defensible way to manage information-security risk rather than an ad hoc collection of tools and good intentions.
- A client is scaling past the point where security depends on one technically-minded founder's personal habits, and needs the responsibility formalized into a system that survives their departure.
- Preparing a client for investor due diligence or an acquisition, where a documented ISMS materially de-risks the deal in the buyer's eyes.
- A client already has security tooling in place (firewalls, access controls, backups) but has never organized it into a risk-assessed, auditable management system — the gap is usually structure and evidence, not raw security capability.

## How it works

### The ISMS core mechanism: risk assessment and treatment

Unlike a fixed checklist, ISO 27001's actual requirement is a risk management *process*: identify information assets, assess the risks to their confidentiality, integrity, and availability, decide how to treat each risk (mitigate, accept, transfer, or avoid), and document that reasoning in a **Statement of Applicability (SoA)** — a formal record of which Annex A controls apply to the organization, which don't, and why. The SoA is the single document an auditor scrutinizes most closely, because it's where the organization's actual risk judgment, not just its control-list compliance, is on record.

### Annex A: 93 controls across four themes (2022 revision)

The 2022 revision restructured what had been 114 controls (2013 edition) into 93 controls organized under four themes — a meaningful simplification consultants working with pre-2022-trained clients should flag explicitly, since older documentation and gap analyses may still reference the old 14-domain, 114-control structure:

| Theme | Approx. control count | Covers |
|---|---|---|
| **Organizational** | 37 | Policies, roles and responsibilities, supplier relationships, incident management, business continuity, compliance |
| **People** | 8 | Screening, terms of employment, security awareness training, disciplinary process, remote working |
| **Physical** | 14 | Secure areas, equipment protection, clear desk/clear screen, physical entry controls |
| **Technological** | 34 | Access control, cryptography, logging and monitoring, network security, secure development, malware protection |

93 controls total (37+8+14+34) — not every organization implements all 93; the SoA is precisely where each control is marked applicable or excluded, with a documented reason.

### High Level Structure (Annex SL)

Like ISO 9001 and ISO 22301, ISO 27001:2022 follows the shared Annex SL ten-clause structure (context, leadership, planning, support, operation, performance evaluation, improvement), which is what allows an organization already certified to another ISO management-system standard to run an integrated system rather than parallel, duplicate governance.

### The certification path

The path mirrors ISO 9001's: gap analysis against the ISMS clauses and Annex A → risk assessment and SoA development → close identified control gaps → internal audit → management review → Stage 1 audit (documentation review) → Stage 2 audit (operational evidence that controls are actually functioning) → certification issued, typically valid three years, with annual surveillance audits and a recertification audit at cycle end.

### Why it matters specifically for SaaS and telemedicine

For a SaaS vendor, ISO 27001 certification is frequently a procurement gate — enterprise security teams increasingly require it (or an equivalent like SOC 2) before a vendor is even permitted into a security-review queue, independent of how good the product itself is. For telemedicine specifically, it sits alongside — not instead of — HIPAA compliance in the US: HIPAA is a legal requirement for handling protected health information, while ISO 27001 is a voluntary, internationally recognized certification that can serve as structural evidence of the underlying security controls a HIPAA risk analysis also requires, and it maps cleanly to frameworks like HITRUST CSF that harmonize the two.

## Example

A telemedicine startup expanding into enterprise health-system contracts is repeatedly asked by prospective customers' security teams for "ISO 27001 or equivalent." A gap analysis finds real security controls already exist (encrypted data at rest, role-based access, incident logging) but nothing is organized into a risk-assessed system, and there's no SoA justifying why certain controls are or aren't in place. Over five months, the company runs a formal risk assessment, builds its SoA (deliberately excluding a small number of Annex A controls — e.g., specific physical-security controls for a data center they don't own, with the reasoning documented as "transferred to cloud provider, evidenced by the provider's own ISO 27001 certificate"), closes the gaps the risk assessment flagged as unacceptable, and passes Stage 1 and Stage 2 audits. Certification removes the "security certification" blocker that had been stalling three enterprise deals in the pipeline.

## Applying it for a client

Start the engagement with the risk assessment, not with Annex A as a checklist — clients (and less experienced consultants) often try to work top-to-bottom through the 93 controls implementing each one uniformly, when the standard's actual requirement is to implement controls in proportion to assessed risk, documented in the SoA. Explicitly confirm which edition (2013's 114 controls vs. 2022's 93) any existing client documentation or a prior consultant's gap analysis was built against, since the restructuring is significant enough that a stale gap analysis will misstate what's actually required. When a vendor or downstream cloud provider already holds their own ISO 27001 certification, use that as documented evidence to legitimately narrow the client's own SoA scope (the "transferred" risk-treatment option) rather than re-implementing controls the provider already covers. For clients also facing HIPAA or SOC 2 requirements, map the overlap explicitly rather than running three separate compliance projects — much of the underlying control work (access control, logging, incident response, encryption) satisfies more than one framework simultaneously.

## Watch-outs

- Don't let a client treat Annex A as a uniform checklist to be fully implemented regardless of actual risk — the standard requires risk-proportionate treatment, documented in the SoA, and an auditor will ask *why* a control was included or excluded, not just whether it was checked off.
- Confirm which edition (2013 vs. 2022) any existing gap analysis, policy templates, or prior certification references — 114 controls versus 93 controls across four themes is a structural difference, not a cosmetic one, and stale documentation built to the old structure will misrepresent current scope.
- Certification is a point-in-time (plus annual surveillance) attestation, not a guarantee against breach — a certified organization can still suffer an incident; what certification actually attests to is that a risk-managed process exists and is followed.
- "ISO 27001 certified" claims should always be checked against scope — a certificate can legitimately cover only part of an organization (one product line, one data center) while marketing implies coverage of the whole business; always ask what's actually in scope.
- Small clients sometimes pursue full ISO 27001 certification when a lighter-weight approach (e.g., aligning to NIST CSF or completing a SOC 2 Type I first) would satisfy the immediate commercial requirement at lower cost — match the framework to the actual ask before committing to the heavier certification path.

## Related

- [iso-9001-qms.md](../operations/iso-9001-qms.md) — shares Annex SL's high-level structure, enabling an integrated management system for a client pursuing both quality and security certification.
- [iso-22301-bcm.md](../operations/iso-22301-bcm.md) — business continuity and information security overlap directly; several Annex A organizational controls concern incident management and continuity.
- [soc2-compliance.md](../operations/soc2-compliance.md) — the more common alternative or complement for US-based SaaS vendors; attestation rather than certification, but covering substantially overlapping ground.
- [nist-csf.md](../operations/nist-csf.md) — a voluntary US framework that maps closely to ISO 27001's control themes without requiring formal certification.
- [hipaa-hitrust.md](../operations/hipaa-hitrust.md) — for telemedicine and healthcare clients, ISO 27001 is one of the frameworks HITRUST CSF harmonizes against HIPAA's legal requirements.
- [vendor-risk-management.md](../operations/vendor-risk-management.md) — a vendor's own ISO 27001 certificate is frequently accepted as due-diligence evidence in a client's third-party risk assessment.
