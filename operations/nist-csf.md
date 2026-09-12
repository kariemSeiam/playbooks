---
domain: operations
concept: NIST Cybersecurity Framework
source: research — NIST Cybersecurity Framework 2.0 (February 2024), National Institute of Standards and Technology
tags: [cybersecurity, risk, nist, framework, governance]
---

# NIST Cybersecurity Framework

The NIST Cybersecurity Framework (CSF) is a voluntary, risk-based framework — not a certification — published by the US National Institute of Standards and Technology to help organizations understand, manage, and communicate cybersecurity risk in a common vocabulary. First published in 2014 (developed in response to a 2013 executive order focused on critical infrastructure), updated to version 1.1 in 2018, and substantially revised as CSF 2.0 in February 2024. A consultant needs this framework because, unlike ISO 27001 or SOC 2, there is nothing to "pass" — CSF is a structuring language for a security program that a client can adopt at any size, and its main value is giving a founder or board a shared, outcome-oriented vocabulary for a conversation ("where are we on Protect vs. Respond") that otherwise stays vague.

## When to use

- A client has no formal security framework at all and needs a starting structure that doesn't require pursuing certification or paying for an external audit to get value from.
- A board or investor asks "what's our cybersecurity posture" and the client has no common vocabulary to answer with beyond listing individual tools.
- Comparing a client's security program against ISO 27001 or SOC 2 requirements — CSF's function structure maps cleanly onto both and can serve as an internal planning layer underneath either certification effort.
- A client wants to set a security risk strategy at the organizational/governance level, not just implement individual technical controls — this is exactly what CSF 2.0's new Govern function is built for.
- Any organization, regardless of sector or size — CSF 2.0's scope was explicitly broadened beyond its original critical-infrastructure focus to fit organizations of any size and sector.

## How it works

### Six functions (2.0 added Govern)

CSF 2.0 organizes cybersecurity outcomes into six functions. The first five existed in 1.1; **Govern** is new in 2.0, and it deliberately wraps around the other five rather than sitting alongside them as a peer, since governance decisions (risk strategy, roles, policy) shape how the other five functions actually get executed:

| Function | What it covers |
|---|---|
| **Govern (GV)** | Establishes and monitors the organization's cybersecurity risk management strategy, expectations, and policy — the "new" function in 2.0, explicitly framed as informing and prioritizing the other five. |
| **Identify (ID)** | Understand the organization's assets, data, systems, and the risks to them — you can't protect what you haven't inventoried. |
| **Protect (PR)** | Implement safeguards to limit or contain the impact of a potential cybersecurity event (access control, training, data security, protective technology). |
| **Detect (DE)** | Find and analyze cybersecurity events as they're happening, through continuous monitoring. |
| **Respond (RS)** | Take action once an incident has been detected — containment, mitigation, communication. |
| **Recover (RC)** | Restore capabilities and services impaired by a cybersecurity incident, and improve based on what happened. |

The practical value of naming Govern separately in 2.0 is that it forces an explicit conversation about *who decides* cybersecurity risk tolerance and strategy at the organization — a gap most small and mid-size clients had never actually assigned before 2.0 gave it a name.

### Implementation Tiers and Profiles

CSF doesn't prescribe a single required maturity level — instead it gives a client two tools to describe where they are and where they want to be:

- **Implementation Tiers** — describe how rigorously an organization manages cybersecurity risk, from **Tier 1 (Partial)** — ad hoc, reactive — through **Tier 2 (Risk Informed)**, **Tier 3 (Repeatable)**, to **Tier 4 (Adaptive)** — continuously improving based on lessons learned and predictive indicators. Tiers describe the *organization's overall risk-management maturity*, not compliance with specific controls.
- **Profiles** — a **Current Profile** (what outcomes the organization achieves today across the six functions) compared against a **Target Profile** (what it needs to achieve, driven by its actual risk tolerance, regulatory obligations, and business objectives). The gap between Current and Target Profile is the client's prioritized action plan.

### Scope broadened in 2.0

CSF was originally developed under a 2013 executive order specifically focused on critical infrastructure sectors (energy, finance, healthcare infrastructure, etc.). CSF 2.0 explicitly broadens its stated scope and language to fit organizations of any size, sector, and cybersecurity maturity level — reflecting how the framework had already been adopted far beyond its original critical-infrastructure audience in practice, and formalizing that broader applicability in the document itself.

### Voluntary, and how it relates to certifiable standards

CSF has no certification body and no pass/fail audit — an organization cannot become "NIST CSF certified." Its value is as an internal planning and communication tool, and as a mapping layer: CSF's six functions map reasonably cleanly onto ISO 27001's Annex A control themes and SOC 2's Trust Services Criteria, which makes it a useful common language for an organization pursuing (or comparing) multiple frameworks at once, even though adopting CSF itself satisfies no external certification requirement on its own.

## Example

An early-stage fintech client has scattered security practices (some access controls, ad hoc incident response, no documented risk strategy) and a board asking "are we secure enough." Rather than jumping straight to ISO 27001 certification (a multi-month, real-cost undertaking), the consultant builds a Current Profile across the six functions — revealing strong Protect-function maturity (the engineering team already does access control and encryption well) but near-zero Govern and Respond maturity (no named risk owner, no documented incident-response runbook). A Target Profile is set at Tier 2 (Risk Informed) for the next two quarters, with the gap-closing plan prioritizing Govern (naming a security risk owner, setting a documented risk appetite) and Respond (writing an incident-response runbook) — both low-cost relative to the value of finally being able to answer the board's question with a structured, specific plan rather than a list of tools.

## Applying it for a client

Use CSF as the fastest, lowest-cost way to give a client structured vocabulary for a security conversation *before* committing to the cost of a certifiable framework like ISO 27001 or SOC 2 — build a quick Current Profile across the six functions, and let the gaps it reveals inform whether the client actually needs formal certification yet or can close the highest-priority gaps informally first. Push Govern specifically for any client who has never named who owns cybersecurity risk strategy at the organization — this is the single most common gap CSF 2.0 was designed to surface, and it's inexpensive to close (naming an owner, documenting a risk appetite) relative to its diagnostic value. When a client is simultaneously pursuing ISO 27001 or SOC 2, use CSF's six functions as an internal planning taxonomy underneath either certification effort, rather than running three separate mental models for what is largely overlapping work.

## Watch-outs

- CSF has no certification — a client or vendor claiming to be "NIST CSF certified" is describing something that doesn't exist as a formal credential; the accurate claim is alignment with, or use of, the framework internally.
- Don't let CSF adoption substitute for a certifiable framework a client actually needs commercially (ISO 27001, SOC 2) — CSF is complementary internal structure, not a replacement for what a specific customer or regulator is contractually requiring.
- Implementation Tiers describe overall risk-management maturity, not a checklist of specific controls implemented — don't let a client conflate "we're Tier 3" with "we've implemented X specific controls."
- Confirm whether a client's existing documentation or a prior consultant's assessment was built against CSF 1.1 or 2.0 — the addition of Govern as a full function (not just a sub-category as it was informally treated pre-2.0) is a structural change, not a minor update.
- A Target Profile set once and never revisited stops reflecting the organization's actual current risk tolerance and threat landscape — treat Profile-setting as a recurring exercise, not a one-time deliverable.

## Related

- [iso-27001-isms.md](../operations/iso-27001-isms.md) — CSF's six functions map reasonably closely onto ISO 27001's Annex A themes, and can serve as an internal planning layer beneath formal certification work.
- [soc2-compliance.md](../operations/soc2-compliance.md) — many controls a SOC 2 audit tests fall directly under CSF's Protect and Detect functions.
- [incident-management-itil-sre.md](../operations/incident-management-itil-sre.md) — CSF's Respond and Recover functions are the framework-level version of the operational incident-management and postmortem practices covered there.
- [iso-22301-bcm.md](../operations/iso-22301-bcm.md) — CSF's Recover function and ISO 22301's business continuity recovery strategies cover substantially the same ground from different framework traditions.
- [vendor-risk-management.md](../operations/vendor-risk-management.md) — CSF is one of the frameworks the Shared Assessments SIG questionnaire explicitly maps its questions against.
