---
name: delivery-handover
description: Compiles a delivery handover package summarizing approved scope, architecture, estimate, and PoC outcomes once the proposal has been accepted by the customer.
---

# Delivery Handover Skill

## Purpose

Package the approved pre-sales artifacts into a concise handover document so the delivery team can start execution
without re-deriving context from scratch.

## When to Use

- Only after the proposal has been marked **accepted** by the user/customer (post Checkpoint #6).

## Required Input

- `engagements/<customer>/03-prd/prd.md`
- `engagements/<customer>/06-architecture/architecture.md`
- `engagements/<customer>/07-estimation/estimation-summary.md`
- `engagements/<customer>/08-poc/poc-results.md` (if available)
- `engagements/<customer>/09-proposal/proposal.md` (accepted)

## Step-by-Step Execution

1. Confirm the proposal status is "Accepted" before proceeding; if not, stop.
2. Summarize final agreed scope (MVP + any accepted change requests) with Requirement/Feature ID references.
3. Carry forward the architecture overview and any PoC outcomes that affect delivery decisions.
4. Carry forward the approved estimate (effort, roles, indicative timeline) as the delivery team's starting
   baseline.
5. List all open questions/assumptions still unresolved at handover, so delivery can prioritize closing them early.
6. Populate `engagements/<customer>/10-handover/handover-package.md`.

## Business Rules

- The handover package must not introduce new scope — it consolidates already-approved artifacts only.
- Any assumption not yet resolved must be clearly listed as a delivery-phase risk, not silently dropped.
- Preserve all traceability IDs so delivery teams can trace stories back to original requirements.

## Output Format

Markdown document: Final Scope Summary, Architecture Summary, Estimate Summary, PoC Outcomes, Open
Items/Assumptions for Delivery, Key Contacts/Stakeholders (if known).

## Quality Validation Checklist

- [ ] Proposal status confirmed as "Accepted" before handover is generated.
- [ ] No new scope introduced beyond what was proposed/accepted.
- [ ] All traceability IDs preserved.
- [ ] Outstanding assumptions/open questions listed as delivery-phase risks.

## Example Usage

> Handover package notes: "FEAT-003 (SSO) accepted as part of MVP; Open Item: customer's IdP configuration details
> still pending — must be resolved in delivery Sprint 1."
