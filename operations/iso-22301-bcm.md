---
domain: operations
concept: ISO 22301 Business Continuity Management
source: research — ISO 22301:2019, International Organization for Standardization
tags: [business-continuity, bcm, disaster-recovery, resilience, iso]
---

# ISO 22301 Business Continuity Management

ISO 22301 is the international standard for a Business Continuity Management System (BCMS) — a documented, auditable set of processes an organization runs to keep delivering its critical products and services, at an acceptable predefined level, during and after a disruption, rather than discovering during an actual crisis that nobody had planned for it. The standard traces back to the British standard BS 25999, was first issued internationally as ISO 22301:2012, and was revised to its current form as ISO 22301:2019. A consultant needs this framework because business continuity is one of the areas where clients most reliably overestimate their own readiness — a plan that exists only as a document nobody has tested is functionally the same as no plan at all when the actual disruption hits.

## When to use

- A client has never formally assessed what would happen to the business if a key system, supplier, location, or person became unavailable for days or weeks.
- A client is being asked by a customer, insurer, or regulator to demonstrate business continuity capability, sometimes as a contractual precondition.
- After a near-miss (an outage, a supplier failure, a local disaster) that exposed how unprepared the organization actually was, and the client wants to formalize a response rather than rely on improvisation next time.
- A client already holds ISO 9001 or ISO 27001 and wants to extend the same management-system discipline (leadership commitment, internal audit, management review) to continuity, at relatively low incremental cost.
- Any client whose business model has a genuine single point of failure — one facility, one key supplier, one critical system — where a continuity gap is a survival-level risk, not a compliance nicety.

## How it works

### Business Impact Analysis (BIA)

The BIA is the foundational exercise: for each critical business activity, the organization determines how much disruption it can actually tolerate, expressed through three specific measures:

| Measure | Definition |
|---|---|
| **RTO (Recovery Time Objective)** | The maximum acceptable time to restore an activity or system after a disruption before the damage becomes unacceptable. |
| **RPO (Recovery Point Objective)** | The maximum acceptable amount of data loss, measured in time — i.e., how far back the last usable backup or checkpoint needs to be. |
| **MTPD (Maximum Tolerable Period of Disruption)** | The absolute outer limit past which the disruption threatens the organization's viability, regardless of recovery effort already underway. |

The BIA forces a specific, numbers-based answer to "how bad can this get before it's unrecoverable" for every critical activity — rather than the vague, universally-optimistic answer most organizations give when nobody has actually done the exercise.

### PDCA applied to continuity

Like ISO 9001, ISO 22301 runs on the Plan-Do-Check-Act cycle: **Plan** — establish continuity policy, objectives, and the BIA/risk assessment that inform them; **Do** — implement and operate the continuity controls and plans; **Check** — monitor, test (via exercises), and review the BCMS's actual effectiveness; **Act** — take corrective action and improve the system based on what Check revealed, including after every real incident or test.

### Annex SL — shared structure with other ISO management systems

ISO 22301:2019 follows the same Annex SL "High Level Structure" as ISO 9001 and ISO 27001 (context of the organization, leadership, planning, support, operation, performance evaluation, improvement). This is a deliberate design choice by ISO: an organization already running an ISO 9001 or ISO 27001 management system already has most of the leadership-commitment, internal-audit, and management-review infrastructure a BCMS needs — the incremental work is mostly the continuity-specific content (BIA, continuity plans, exercising), not rebuilding governance from scratch.

### What a business continuity plan actually contains

A BCP built to satisfy ISO 22301 goes beyond a generic "in case of emergency" document and includes:

- **Incident response procedures** — the immediate, first-hours actions when a disruption is detected.
- **Crisis management structure** — who has authority to declare an incident, activate the plan, and make decisions under pressure, named in advance rather than improvised in the moment.
- **Disaster recovery procedures** — the technical/IT-specific restoration steps (a subset of the broader BCP, focused specifically on systems and data).
- **Communication plan** — pre-drafted internal and external messaging, including who notifies customers, staff, regulators, and media, and in what order.
- **Recovery strategies per critical activity**, each sized against the RTO/RPO/MTPD figures the BIA established for it.

### Exercising and the certification path

A BCMS is only as good as its last real test — ISO 22301 explicitly requires exercising the plan (tabletop walkthroughs, simulations, or full-scale drills) as part of the Check phase, not just writing it. Certification itself follows the same general path as ISO 9001 and ISO 27001: gap analysis, internal audit, management review, Stage 1 (documentation) and Stage 2 (operational evidence) external audits, a three-year certificate with annual surveillance audits, and recertification at cycle end.

## Example

A regional logistics company runs its entire dispatch operation through one cloud system hosted by a single vendor and out of one physical dispatch office. A BIA reveals dispatch has an RTO of 4 hours (beyond that, committed same-day deliveries start failing contractually) and an RPO of 15 minutes (losing more than that much dispatch data means re-confirming every in-flight order manually). Before the BIA, the company had no documented fallback if the office became unusable — the exercise itself, run as a tabletop simulation of "the dispatch office is unreachable for a full day," is what first surfaces that no one currently knows how to redirect dispatch calls, and that the current backup cadence for the cloud system doesn't actually meet the 15-minute RPO. The resulting plan adds a documented remote-dispatch fallback, tightens the backup interval, and names, in advance, who has authority to activate the fallback — closing a gap that had been invisible until the first exercise forced it into the open.

## Applying it for a client

Start with the BIA, not with writing a plan — a continuity plan built before the organization has actually quantified its RTO/RPO/MTPD per critical activity is guessing at what "acceptable disruption" means, and will either over-invest in protecting something that could tolerate a longer outage or under-invest in something that can't. Push every client toward at least one real exercise before calling a BCMS "done" — a plan that has only ever existed on paper reliably fails in ways a tabletop walkthrough would have caught for a fraction of the cost of discovering them during an actual incident. If a client already holds ISO 9001 or ISO 27001, explicitly reuse the existing leadership-commitment and internal-audit machinery under Annex SL rather than building parallel governance — this materially lowers the incremental cost of adding 22301.

## Watch-outs

- A business continuity plan that has never been exercised is closer to a comforting fiction than a real capability — insist on at least a tabletop drill, and treat what it reveals as required input to the next plan revision, not a formality to check off.
- Disaster recovery (IT/systems restoration) is a subset of business continuity, not a substitute for it — a client with a solid backup/DR process for their servers can still have zero plan for the human and operational side of a disruption (who communicates what, to whom, and who has authority to decide).
- RTOs set optimistically, without honestly checking them against what the organization can actually deliver technically and operationally, create a false sense of security that collapses exactly when it's tested for real.
- Certification and genuine resilience are not the same claim — a client can pass a Stage 2 audit on paper-adequate plans that were never realistically exercised; push past the audit-minimum toward plans the client would actually trust in a real event.
- Single-point-of-failure risks (one vendor, one office, one key person) are the ones a BIA is specifically designed to surface — don't let a BIA stay abstract; name the organization's actual single points of failure explicitly and size RTO/RPO against each one.

## Related

- [iso-9001-qms.md](../operations/iso-9001-qms.md) — shares the same Annex SL structure and PDCA cycle; a client with 9001 already has most of the governance infrastructure a BCMS needs.
- [iso-27001-isms.md](../operations/iso-27001-isms.md) — information security incidents and business continuity overlap directly; ISO 27001's Annex A includes ICT readiness for business continuity as a control area.
- [incident-management-itil-sre.md](../operations/incident-management-itil-sre.md) — incident response and crisis management procedures in a BCP are the operational front line that a mature incident-management practice feeds into and informs.
- [nist-csf.md](../operations/nist-csf.md) — the Recover function in NIST CSF covers much of the same ground as ISO 22301's recovery strategies, from a US-framework rather than certifiable-standard angle.
