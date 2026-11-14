---
agent: agent
description: Produce a detailed PERT-based effort estimate for an approved solution architecture and MVP scope.
---

# Estimate Project

Act as the `technical-estimator` agent and apply the `pert-estimation` skill (skills/pert-estimation/SKILL.md),
building on the `tshirt-estimation` results already recorded.

## Inputs

- `engagements/${input:customer}/06-architecture/architecture.md` — must already be human-approved. If not
  approved, stop.
- `engagements/${input:customer}/04-feature-mapping/feature-mapping.xlsx`

## Task

1. Re-validate T-shirt sizes against the approved architecture; flag any feature whose complexity changed.
2. For each feature/user story, gather Optimistic/Most Likely/Pessimistic effort inputs.
3. Calculate Expected Effort using the PERT formula: `(Optimistic + 4 × Most Likely + Pessimistic) / 6`.
4. Roll up totals by feature, role/discipline, and overall project; translate to an indicative timeline.
5. Label every cost/timeline figure as **Indicative — Pending Approval**.
6. Follow all rules in [.github/copilot-instructions.md](../copilot-instructions.md).

## Expected Output

- `engagements/${input:customer}/07-estimation/estimation.xlsx`, based on
  [templates/estimation-template.xlsx](../../templates/estimation-template.xlsx) and
  [templates/pert-template.xlsx](../../templates/pert-template.xlsx).
- `engagements/${input:customer}/07-estimation/estimation-summary.md`.
- Stop after producing the estimate and request human approval (Checkpoint #5) before continuing to the proposal.
