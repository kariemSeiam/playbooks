---
domain: operations
concept: SOC 2 Compliance
source: research — AICPA Trust Services Criteria (2017, revised 2022)
tags: [compliance, audit, trust-services, saas, security]
---

# SOC 2 Compliance

SOC 2 (System and Organization Controls 2) is an attestation report — not a certification — issued by a licensed independent CPA firm, confirming that a service organization's controls meet the American Institute of Certified Public Accountants' (AICPA) Trust Services Criteria. The distinction between "attestation" and "certification" matters more than it sounds: there is no pass/fail badge and no universal checklist every company satisfies identically — the auditor examines the specific controls the organization itself claims to have, and the report describes what was tested and what, if anything, didn't hold up, rather than issuing a simple certificate. A consultant needs this framework because SOC 2 has become the default trust currency for US-based (and increasingly global) SaaS companies — it is frequently the first document an enterprise prospect's security team asks for, well before evaluating the product itself.

## When to use

- A SaaS or platform client is losing or stalling enterprise deals because prospects' security or procurement teams require a SOC 2 report before proceeding.
- A client needs to decide between pursuing Type I (faster, cheaper, proves design) or Type II (slower, more expensive, proves the controls actually worked over time) based on their sales cycle urgency versus the depth of assurance customers actually need.
- A client is scaling past informal security practices and needs a structured, externally validated basis for the controls they claim to have.
- Comparing a client's compliance options — SOC 2 versus ISO 27001 versus a lighter self-attestation — when only one is commercially necessary right now.

## How it works

### Type I vs. Type II

| | Type I | Type II |
|---|---|---|
| **What it proves** | Controls are suitably *designed* as of a specific point in time. | Controls are suitably designed *and operated effectively* over an observation period. |
| **Typical observation period** | None — a single point-in-time snapshot. | Commonly 3 to 12 months, most often 6 months for a first report. |
| **Speed to first report** | Faster — can often be achieved in weeks to a couple of months. | Slower — requires the full observation period to elapse before the audit can even begin. |
| **What buyers actually weight it as** | A useful first step, but recognized as weaker evidence. | The report most enterprise security teams actually require before trusting a vendor with sensitive data. |

A common and sound sequencing for a client under sales pressure: pursue Type I first to have *something* to show prospects quickly, while simultaneously starting the Type II observation period, so the stronger report follows a few months later without restarting the whole process.

### The five Trust Services Criteria (categories)

SOC 2 is scoped around five categories; only **Security** is mandatory (it's referred to as the "Common Criteria," since every SOC 2 report includes it), and the organization chooses which of the remaining four to include based on what's actually relevant to its service:

| Category | Mandatory? | Covers |
|---|---|---|
| **Security** | Yes (Common Criteria) | Protection against unauthorized access, both physical and logical — the baseline every report includes. |
| **Availability** | Optional | The system is available for operation and use as committed or agreed (relevant for anything with an uptime SLA). |
| **Processing Integrity** | Optional | System processing is complete, valid, accurate, timely, and authorized (relevant for transaction- or calculation-heavy systems, e.g., payments, billing). |
| **Confidentiality** | Optional | Information designated as confidential is protected as committed or agreed (relevant when handling client business data, contracts, IP). |
| **Privacy** | Optional | Personal information is collected, used, retained, disclosed, and disposed of in conformity with the organization's privacy notice (relevant when handling personal/consumer data specifically). |

Scoping the right optional categories matters commercially — including a category the client's service doesn't actually implicate adds audit cost and scope for no buyer-facing benefit, while omitting one a specific customer actually cares about (e.g., a healthcare-adjacent client skipping Privacy) can stall exactly the deal the report was meant to unblock.

### The audit process

1. **Readiness assessment** — often run informally or by a consultant/compliance platform, comparing current controls against the chosen Trust Services Criteria before the formal audit begins.
2. **Gap remediation** — closing identified control gaps (access reviews, logging, incident response documentation, vendor management, etc.).
3. **Observation period** (Type II only) — the controls must actually operate, evidenced, for the full window before the audit can assess them.
4. **Fieldwork audit** — the licensed CPA firm tests the controls directly: reviewing evidence, interviewing staff, sampling logs and access records.
5. **Report issuance** — the auditor's opinion, plus a detailed description of the system and controls tested, is delivered as the SOC 2 report itself (not a public certificate — it's typically shared under NDA with prospective customers, not published).

## Example

A B2B SaaS company closing its first enterprise deals hits a wall: every prospect's security questionnaire asks for a SOC 2 report, and the company has none. Given sales urgency, it pursues Type I first (Security only, since the product carries no uptime SLA commitment yet and processes no payments directly), completing it in about six weeks and using it to unblock deals already in the pipeline that only required "evidence of a security program." Simultaneously, it begins the observation period for a Type II report covering Security and Availability (added once the company signs its first SLA-backed contract), completing that report roughly six months later — at which point it can satisfy the more rigorous enterprise buyers who explicitly require Type II before signing.

## Applying it for a client

Scope the Trust Services Criteria to what the client's service actually does, not to what "looks thorough" — a client with no uptime commitment doesn't need Availability in scope, and adding it anyway only inflates audit cost and time without a buyer ever asking for it. When a client is under sales pressure, sequence Type I now and Type II observation running concurrently, rather than waiting for a "perfect" Type II report before showing customers anything — a Type I report today plus a committed Type II timeline often satisfies a prospect's security team well enough to keep a deal moving. Read the actual report with the client rather than treating "we got our SOC 2" as binary — reports can include "exceptions" (documented instances where a control didn't operate as designed during the period), and a client should understand and be ready to explain any exception rather than be surprised when a prospect's security reviewer finds it.

## Watch-outs

- SOC 2 is an attestation, not a certification — there is no universal pass/fail, and "SOC 2 compliant" as a marketing claim is often imprecise; the accurate claim is having a SOC 2 report, for a specific scope and period, potentially containing exceptions.
- A Type I report is meaningfully weaker evidence than Type II, and increasingly sophisticated enterprise buyers know the difference — don't let a client present a Type I report as equivalent to Type II in sales conversations.
- Scoping in optional Trust Services Criteria the business doesn't need adds real audit cost and time without adding buyer-facing value — but scoping out one a target customer segment specifically cares about (Privacy for consumer-data businesses, Processing Integrity for fintech) can stall exactly the deals the report exists to unblock.
- SOC 2 reports are typically shared under NDA with specific prospects, not published publicly — don't assume it functions like a public badge the way an ISO certificate can be referenced or displayed.
- The report can include noted exceptions and still be a valid, useful report — a client should never hide an exception from a prospect who asks; misrepresenting or concealing one is a much bigger trust problem than the exception itself.

## Related

- [iso-27001-isms.md](../operations/iso-27001-isms.md) — the more internationally recognized alternative or complement; ISO 27001 is a formal certification against a broader control set, while SOC 2 is a US-centric attestation more common in SaaS sales cycles specifically.
- [nist-csf.md](../operations/nist-csf.md) — many of the underlying controls a SOC 2 audit tests map directly onto NIST CSF's Protect and Detect functions.
- [vendor-risk-management.md](../operations/vendor-risk-management.md) — a vendor's SOC 2 report is one of the most commonly requested pieces of evidence in a client's own third-party risk assessment process.
- [incident-management-itil-sre.md](../operations/incident-management-itil-sre.md) — SOC 2's Security criteria include incident-detection and response controls that a mature incident-management practice directly evidences.
