---
name: pert-estimation
description: Calculates detailed effort estimates per feature using PERT (Program Evaluation and Review Technique) once architecture and scope are well understood.
---

# PERT Estimation Skill

## Purpose

Produce a defensible, detailed effort estimate per feature/user story using PERT, once the solution architecture is
approved and scope is well understood — replacing early T-shirt sizing with calculated expected effort.

## When to Use

- After the solution architecture is human-approved (Checkpoint #4).
- Whenever a feature's scope or complexity changes materially and needs re-estimation.

## Required Input

- `engagements/<customer>/04-feature-mapping/feature-mapping.xlsx` (with T-shirt sizes and technical complexity).
- `engagements/<customer>/06-architecture/architecture.md` (approved).

## Step-by-Step Execution

1. For each feature/user story, gather three effort inputs (in person-days or person-hours, consistent unit across
   the engagement):
   - **Optimistic (O)** — best-case effort if everything goes smoothly.
   - **Most Likely (M)** — realistic effort given known complexity/risks.
   - **Pessimistic (P)** — worst-case effort if significant issues arise.
2. Validate `O ≤ M ≤ P`; if violated, correct the inputs before proceeding.
3. Calculate Expected Effort using the PERT formula:
   $$ E = \frac{O + 4M + P}{6} $$
4. Optionally calculate standard deviation ($\sigma = \frac{P - O}{6}$) to express estimate confidence/risk.
5. Populate [`templates/pert-template.xlsx`](../../../templates/pert-template.xlsx), which auto-calculates Expected
   Effort via formula.
6. Roll up Expected Effort totals into [`templates/estimation-template.xlsx`](../../../templates/estimation-template.xlsx)
   by feature, role/discipline, and overall project.

## Business Rules

- Always use the exact formula `(O + 4M + P) / 6` — never approximate or round ad hoc.
- O, M, P must be elicited from whoever is accountable for delivering that type of work; do not fabricate them.
- Present all rolled-up totals as **indicative effort**, not a committed cost or date, until commercial approval.

## Output Format

`pert-estimation.xlsx` rows: Feature ID, O, M, P, Expected Effort (formula), Std Dev (formula), Notes/Risk.

## Quality Validation Checklist

- [ ] Every row satisfies O ≤ M ≤ P.
- [ ] Expected Effort is computed via formula, not manually typed in.
- [ ] Units (hours/days) are consistent across the whole engagement.
- [ ] Rolled-up totals are labeled "Indicative — Pending Approval".

## Example Usage

> FEAT-003 (SSO): O=3 days, M=5 days, P=10 days → Expected Effort = (3 + 4×5 + 10) / 6 = 5.5 days.
