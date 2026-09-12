---
domain: operations
concept: HIPAA and HITRUST
source: research — Health Insurance Portability and Accountability Act (1996), enforced by HHS Office for Civil Rights; HITRUST CSF v11.x
tags: [healthcare, privacy, hipaa, hitrust, phi, compliance]
---

# HIPAA and HITRUST

HIPAA (the Health Insurance Portability and Accountability Act, 1996) is US federal law setting the legal floor for how Protected Health Information (PHI) must be handled, enforced by the Department of Health and Human Services' Office for Civil Rights (OCR). HITRUST CSF (Common Security Framework) is a private, certifiable framework — now in version 11.x — built specifically to help organizations demonstrate compliance with HIPAA (and several other standards at once) through a single harmonized assessment. The distinction a consultant must never blur: HIPAA is a legal requirement with no formal "certification" issued by the government, while HITRUST is a voluntary, private-sector certification that maps to HIPAA's requirements but is not itself endorsed or recognized by OCR. Any client-facing claim of being "HIPAA certified" is, strictly, inaccurate — the correct claim is "HIPAA compliant" (a legal self-assessment) or "HITRUST certified" (a specific, named private certification that maps to HIPAA among other frameworks).

## When to use

- A telemedicine, digital health, or health-tech client handles PHI and needs its legal obligations under HIPAA translated into an actual operating program, not just a policy binder.
- A client is asked by a healthcare-system customer, payer, or investor for HITRUST certification specifically, rather than a generic "we're HIPAA compliant" assurance.
- Structuring vendor relationships where a client (or its own vendors) will touch PHI — this is exactly where a Business Associate Agreement (BAA) becomes legally mandatory, not optional.
- A client has experienced, or wants to prevent, a reportable breach of PHI and needs the Breach Notification Rule's actual obligations mapped to their specific situation.
- Comparing compliance investment options for a health-tech client already pursuing ISO 27001 or SOC 2 — HITRUST's harmonized structure can reduce duplicated audit effort across frameworks.

## How it works

### HIPAA's three operative rules

| Rule | What it requires |
|---|---|
| **Privacy Rule** | Sets standards for when and how PHI can be used and disclosed, and gives patients rights over their own health information (access, amendment, accounting of disclosures). |
| **Security Rule** | Specifically covers *electronic* PHI (ePHI), requiring administrative, physical, and technical safeguards — this is the rule most directly relevant to a software/health-tech client's actual system architecture. |
| **Breach Notification Rule** | Requires notifying affected individuals, HHS, and in larger breaches the media, within specified timeframes after discovering a breach of unsecured PHI. |

The Security Rule's three safeguard categories are where a health-tech consultant spends most of their time:

- **Administrative safeguards** — risk analysis (a specific, required, ongoing activity — not a one-time task), workforce training, access management policies, a designated security official.
- **Physical safeguards** — facility access controls, workstation security, device and media controls (including secure disposal).
- **Technical safeguards** — access controls (unique user IDs, automatic logoff), audit controls (logging), integrity controls, transmission security (encryption in transit).

### Covered entities, business associates, and BAAs

HIPAA's obligations attach to two categories of organization: **covered entities** (health plans, healthcare clearinghouses, and healthcare providers who transmit health information electronically) and **business associates** (any vendor or subcontractor that creates, receives, maintains, or transmits PHI on a covered entity's behalf — this is where most SaaS/health-tech vendors sit). Whenever a covered entity and a business associate (or two business associates) exchange PHI, a **Business Associate Agreement (BAA)** is legally required — a signed contract specifying how the receiving party will safeguard the PHI, report breaches, and limit its use. A client that handles PHI without a BAA in place with every relevant vendor and customer is out of legal compliance regardless of how good its technical security otherwise is.

### HITRUST CSF: what it actually is

HITRUST CSF is a certifiable framework maintained by the HITRUST Alliance, built to harmonize and cross-reference multiple standards and regulations into a single controls set and assessment — commonly cited as mapping to HIPAA, NIST 800-53, ISO 27001, PCI DSS, and GDPR, among others. Its practical appeal is that one HITRUST assessment produces evidence that can be mapped back to satisfy multiple separate compliance asks at once, rather than an organization running a separate audit for each framework its various customers happen to require. HITRUST offers assessment levels of increasing rigor (commonly a lighter "e1" essentials assessment, a mid-tier "i1" implemented assessment, and the more comprehensive "r2" risk-based, 2-year certification, in the current version's naming), letting an organization match assessment depth to its actual risk profile and customer demands.

### The critical distinction: HITRUST is not government-endorsed

HITRUST certification is a private-sector credential. It is not issued, endorsed, or recognized by HHS or OCR as an official "HIPAA certification" — no such official government certification exists for HIPAA at all. A HITRUST r2 certification is strong, credible evidence that an organization's controls map to HIPAA's requirements (among others), and many healthcare-system customers treat it as sufficient assurance in vendor due diligence — but a consultant must be precise with a client about what the credential legally represents versus what it's colloquially treated as in the market.

## Example

A telemedicine startup handling patient records and video consultations needs to formalize compliance before signing its first hospital-system customer. It maps its Security Rule obligations concretely: administrative (a documented risk analysis, now run annually rather than the ad hoc review it had been doing), physical (its cloud hosting provider's own physical safeguards, carried forward via a BAA with that provider), and technical (encryption in transit and at rest, unique per-clinician logins with automatic session timeout, and centralized audit logging of every PHI access). It signs BAAs with its cloud host, its customer-support ticketing vendor (which sees PHI in support tickets), and each hospital-system customer. When the hospital system's procurement team specifically asks for HITRUST rather than a self-attestation of HIPAA compliance, the company pursues an i1 assessment as a proportionate middle tier, given its size and the specific ask — rather than immediately jumping to the more expensive r2 certification the largest enterprise customers eventually require.

## Applying it for a client

Start by mapping exactly where PHI flows through the client's systems and vendors — every one of those flows needs either a direct HIPAA obligation (if the client is itself a covered entity or business associate) or a BAA (if a third party is involved), and clients routinely miss vendors that touch PHI incidentally (a support-ticketing tool, an analytics vendor, a transcription service) because they don't think of themselves as "healthcare vendors." Treat the Security Rule's risk analysis as a recurring, dated activity, not a document written once at founding — an outdated risk analysis is one of OCR's most commonly cited enforcement findings. Before recommending a HITRUST pursuit, confirm which specific ask is actually driving it (a particular hospital-system customer's procurement requirement, versus a general "we should be more compliant" instinct) and match the assessment tier (e1/i1/r2) to that specific ask and the client's size, rather than defaulting to the most rigorous and expensive tier. Always correct any client instinct to market themselves as "HIPAA certified" — redirect the language to "HIPAA compliant" (a legal self-assessment claim) or the specific HITRUST tier actually achieved.

## Watch-outs

- There is no such thing as an official government "HIPAA certification" — a client or their marketing team claiming to be "HIPAA certified" is making an inaccurate claim that a sophisticated healthcare-system buyer's compliance team will notice and flag.
- HITRUST is a private, voluntary certification, not an OCR-endorsed one — it's strong market-accepted evidence of HIPAA alignment, but a consultant should never represent it to a client as legally equivalent to, or a substitute for, the underlying legal HIPAA compliance obligation itself.
- A missing BAA with even one vendor that incidentally touches PHI is a real compliance gap, not a technicality — audit every vendor relationship for PHI exposure, not just the obviously "healthcare" ones.
- The Security Rule's risk analysis requirement is ongoing, not a one-time deliverable — a risk analysis performed once at company founding and never updated is one of the most common gaps OCR enforcement actions cite.
- Assessment-tier selection (HITRUST e1/i1/r2) should be driven by the client's actual size, risk, and customer requirements — over-buying an r2 certification for a small startup's first customer relationship burns budget disproportionate to what's actually being asked for.

## Related

- [iso-27001-isms.md](../operations/iso-27001-isms.md) — one of the frameworks HITRUST CSF harmonizes against HIPAA; a client's existing ISO 27001 controls substantially reduce the incremental HITRUST assessment effort.
- [soc2-compliance.md](../operations/soc2-compliance.md) — often pursued alongside HIPAA/HITRUST for health-tech SaaS vendors; overlapping controls (access management, encryption, incident response) satisfy both simultaneously.
- [vendor-risk-management.md](../operations/vendor-risk-management.md) — BAAs and vendor PHI-flow mapping are a direct application of third-party risk management to the healthcare-specific legal context.
- [nist-csf.md](../operations/nist-csf.md) — NIST 800-53, which HITRUST also harmonizes against, is closely related in lineage to the NIST Cybersecurity Framework's control philosophy.
