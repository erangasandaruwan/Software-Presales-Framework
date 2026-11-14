---
name: proposal-generation
description: Assembles a customer-facing proposal from approved PRD, architecture, and estimation artifacts, preserving traceability and indicative labeling of commercial figures.
---

# Proposal Generation Skill

## Purpose

Compile a polished, customer-facing proposal strictly from already-approved upstream artifacts (PRD, architecture,
estimate), preserving traceability and correctly labeling commercial figures as indicative pending approval.

## When to Use

- After PRD, architecture, and estimate have all received human approval (Checkpoints #2, #4, #5).
- When a proposal needs revision following customer feedback or re-estimation.

## Required Input

- `engagements/<customer>/03-prd/prd.md` (approved)
- `engagements/<customer>/06-architecture/architecture.md` (approved)
- `engagements/<customer>/07-estimation/estimation-summary.md` (approved)
- `engagements/<customer>/08-poc/poc-results.md` (if available)

## Step-by-Step Execution

1. Write an Executive Summary describing the customer's problem and proposed solution in business language.
2. Summarize scope from the PRD/MVP — list included features with Requirement ID references available on request.
3. Summarize the solution overview from the architecture document, in a business-readable form (avoid deep
   technical jargon unless the audience is technical).
4. Insert the commercial section from the approved estimate, converting effort to indicative cost using the
   engagement's agreed rate card (only if provided/confirmed — otherwise leave as effort-only and flag as Open
   Question).
5. Include any PoC outcomes relevant to de-risking the proposal.
6. List assumptions and open questions the customer should be aware of.
7. Populate [`templates/proposal-template.md`](../../../templates/proposal-template.md).

## Business Rules

- No cost or date may appear that isn't traceable to the approved estimate/architecture.
- Mark the commercial section **Indicative — Subject to Final Commercial Approval** unless the user has explicitly
  signed off on final figures.
- Do not omit material assumptions/open questions to make the proposal look more certain than it is.

## Output Format

Markdown document per `proposal-template.md`: Executive Summary, Scope & MVP, Solution Overview, Commercial Summary
(indicative), Assumptions & Open Questions, Next Steps.

## Quality Validation Checklist

- [ ] Every scope item traces to an approved PRD feature.
- [ ] Every cost/timeline figure traces to the approved estimate.
- [ ] Commercial section is labeled indicative unless explicitly approved as final.
- [ ] Assumptions/open questions are disclosed, not hidden.

## Example Usage

> Commercial Summary: "Indicative effort: 42 person-days (Indicative — Subject to Final Commercial Approval).
> Based on PERT estimate dated 2026-11-01."
