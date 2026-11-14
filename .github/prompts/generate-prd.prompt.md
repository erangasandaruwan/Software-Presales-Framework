---
agent: agent
description: Generate a Product Requirements Document (PRD) from an approved requirements baseline.
---

# Generate PRD

Act as the `product-manager` agent and apply the `prd-generation` skill (skills/prd-generation/SKILL.md).

## Inputs

- `engagements/${input:customer}/02-requirements/requirements-baseline.md` — must already be human-approved. If it
  is not approved, stop and say so instead of proceeding.

## Task

1. Group related requirements into capability areas and describe goals, in-scope behavior, and out-of-scope notes.
2. Carry forward all Requirement IDs, and preserve Confirmed/Assumed/Open Question status.
3. Produce a dedicated Non-Functional Requirements section grouped by type.
4. Follow all rules in [.github/copilot-instructions.md](../copilot-instructions.md) — do not introduce new
   scope not present in the baseline.

## Expected Output

- `engagements/${input:customer}/03-prd/prd.md`, structured per [templates/prd-template.md](../../templates/prd-template.md).
- Stop after producing the PRD and request human approval (Checkpoint #2) before continuing to feature mapping.
