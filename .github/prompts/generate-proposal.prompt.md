---
agent: agent
description: Assemble the customer-facing proposal from approved PRD, architecture, and estimate artifacts.
---

# Generate Proposal

Act as the `proposal-writer` agent and apply the `proposal-generation` skill (skills/proposal-generation/SKILL.md).

## Inputs

- `engagements/${input:customer}/03-prd/prd.md` — must be approved.
- `engagements/${input:customer}/06-architecture/architecture.md` — must be approved.
- `engagements/${input:customer}/07-estimation/estimation-summary.md` — must be approved.
- `engagements/${input:customer}/08-poc/poc-results.md` (if available).

If any required input is missing or not yet approved, stop and state which one.

## Task

1. Write an Executive Summary in business language.
2. Summarize scope from the PRD/MVP, referencing Requirement/Feature IDs.
3. Summarize the solution overview from the architecture document.
4. Insert the commercial section from the approved estimate, labeled **Indicative — Subject to Final Commercial
   Approval** unless the user has explicitly signed off on final figures.
5. List assumptions and open questions.
6. Follow all rules in [.github/copilot-instructions.md](../copilot-instructions.md).

## Expected Output

- `engagements/${input:customer}/09-proposal/proposal.md`, based on
  [templates/proposal-template.md](../../templates/proposal-template.md).
- Stop after producing the proposal and request human approval (Checkpoint #6) before marking it ready to send to
  the customer.
