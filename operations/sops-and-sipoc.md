---
domain: operations
concept: SOPs and SIPOC
source: research — American Society for Quality (ASQ) process documentation practice; SIPOC methodology from Six Sigma/TQM tradition
tags: [procedures, documentation, process-mapping, sipoc, standardization]
---

# SOPs and SIPOC

A Standard Operating Procedure (SOP) is a written, step-by-step instruction that tells anyone qualified to do a task exactly how to do it the same way every time, so the outcome doesn't depend on who happens to be doing it. A SIPOC diagram (Suppliers–Inputs–Process–Outputs–Customers) is a single-page tool for scoping a process at a high level *before* anyone writes the detailed SOP for it — it names, in five columns, who supplies the process, what goes in, the handful of major steps, what comes out, and who receives it. A consultant needs both because they solve different problems at different altitudes: SIPOC answers "what is this process and where does it start and stop," and the SOP answers "exactly how does a person execute step 3 of it" — and skipping the SIPOC step is exactly how organizations end up writing detailed procedures for the wrong process boundaries.

## When to use

- A founder-led business is scaling past the point where "the founder just knows how it's done" is a viable operating model — the knowledge needs to leave the founder's head and become a document.
- A client is experiencing inconsistent quality or output across shifts, locations, or staff members doing "the same" job differently.
- Before starting any formal process-improvement project (Lean Six Sigma, ISO certification work) — SIPOC is the standard first artifact used to agree on process scope before deeper analysis begins.
- Onboarding new hires faster, or preparing a business for a founder's planned absence (illness, vacation, exit) without operations collapsing.
- Preparing for a certification audit (ISO 9001, SOC 2, ISO 27001) where documented, evidenced procedures are an explicit requirement, not optional polish.

## How it works

### Building the SIPOC first

SIPOC is built in a specific, counter-intuitive order — starting from the middle, not the left:

1. **Process** — name the 4-7 major steps of the process at a high level (not detailed enough to be a flowchart; if a box needs sub-steps, it's too granular for SIPOC).
2. **Outputs** — what does this process produce, physically or as information/service?
3. **Customers** — who receives each output — internal (the next department) or external (the paying customer)?
4. **Inputs** — working backward from Process, what must arrive before step 1 can start?
5. **Suppliers** — who or what provides each input — internal or external?

| Suppliers | Inputs | Process | Outputs | Customers |
|---|---|---|---|---|
| Who provides what the process needs | What must arrive before the process can start | The 4-7 major steps, high level only | What the process produces | Who receives each output |

The reason to build Process and Outputs before Suppliers and Inputs is that most teams already know what they're supposed to produce, but routinely discover — only by working backward — an input or a supplier they'd been assuming existed without ever confirming it, or a dependency nobody had actually named.

### Writing the SOP that follows

Once SIPOC has scoped a specific process box, the SOP documents that one box in operational detail. A complete SOP contains:

- **Purpose** — why this procedure exists and what outcome it guarantees.
- **Scope** — exactly which situations it covers, and — just as important — which it explicitly does not.
- **Roles and responsibilities** — who is authorized or expected to perform each step.
- **Step-by-step procedure** — numbered, sequential, written at the level of detail where a competent new hire could follow it without needing to ask a follow-up question.
- **References/related documents** — forms, checklists, or other SOPs it depends on or feeds into.
- **Revision history** — version number, date, author, and what changed — because an undated, unversioned SOP is a document nobody can trust is still current.

### Three levels, not one document type

Organizations conflate three levels of documentation that actually serve different readers:

| Level | Answers | Audience |
|---|---|---|
| **Policy** | Why do we do this at all, and what are the boundaries? | Managers, auditors |
| **Procedure (SOP)** | What are the steps, in order, and who does each? | The person doing the work |
| **Work instruction** | Exactly how do I operate this specific tool/system/form? | A new hire on their first day |

Writing one document that tries to be all three at once is a common failure mode — it ends up too abstract to actually execute from, and too detailed to explain to an auditor why the policy exists.

## Example

A small subscription-box company's fulfillment process, scoped with SIPOC before writing any SOPs:

| Suppliers | Inputs | Process | Outputs | Customers |
|---|---|---|---|---|
| Warehouse team, packaging vendor, customer database | Pick list, boxes/packaging materials, shipping labels | 1. Pull items from shelf → 2. Pack box → 3. Print/apply label → 4. Stage for pickup → 5. Hand off to courier | Packed, labeled, ready-to-ship box | Subscriber (end customer), courier |

From this, the team writes one SOP per process box that actually varies by staff member today — say, "Pack Box" — specifying exact packing order, cushioning requirements per product category, and the quality check before sealing. They do *not* write a SOP for "Pull items from shelf," because that step turns out, on inspection, to already be identical regardless of who does it — SIPOC's value here was showing the team where standardization was actually needed versus already achieved.

## Applying it for a client

Always run SIPOC before writing a single SOP — a client who jumps straight to documenting procedures without first agreeing on process scope routinely documents the wrong boundary (too broad, too narrow, or missing a supplier/input dependency nobody had named) and has to redo the work later. Once SIPOC is built, prioritize which process boxes actually need a written SOP by asking where output varies today by *who* is doing the work — a step that already produces identical results regardless of staff doesn't need a procedure yet, and writing one anyway is wasted documentation effort. For a client preparing for a certification audit, use the SOP's revision-history field as a forcing function: an auditor will ask "when was this last reviewed," and a client with no answer has effectively no document, however detailed it reads.

## Watch-outs

- SIPOC is deliberately high-level — if a client's "Process" column has more than about seven boxes, or contains detailed sub-steps, they've drifted into flowcharting a different tool should handle, not SIPOC.
- An SOP nobody has opened since it was written is not a live document — it's an artifact for the file cabinet, and it will be wrong by the time someone actually needs it; tie every SOP to a review cadence and an owner.
- Don't let a policy document masquerade as an SOP — a document that explains "why we care about quality" without a numbered, executable step sequence will not actually help a new hire do the task.
- Over-documenting a process that changes constantly (early-stage, still-being-invented workflows) creates more maintenance burden than value — SOPs earn their cost once a process has stabilized enough to be worth freezing in writing.
- SIPOC scoping done once at project kickoff and never revisited will silently drift out of date as the client adds new suppliers, channels, or customer segments — treat it as a living reference, not a one-time diagram.

## Related

- [lean-six-sigma.md](../operations/lean-six-sigma.md) — SIPOC is the standard tool used in DMAIC's Define phase to scope a process before deeper analysis.
- [value-chain.md](../operations/value-chain.md) — SIPOC operates at a narrower altitude than the value chain; it's the tool for scoping one specific process, where the value chain scopes the whole business.
- [iso-9001-qms.md](../operations/iso-9001-qms.md) — documented procedures and process ownership are explicit requirements of an ISO 9001 quality management system.
