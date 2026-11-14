---
name: poc-development
description: Selects and scopes high-value proof-of-concept candidates to de-risk the highest-uncertainty technical elements of a proposed solution.
---

# PoC Development Skill

## Purpose

Identify and scope a small number of high-value proof-of-concept (PoC) efforts that validate the riskiest technical
assumptions in the proposed architecture, before full commercial commitment.

## When to Use

- After architecture risks/open technical questions have been identified by the Solution Architect.
- When the customer or internal reviewers require technical validation before finalizing the estimate/proposal.

## Required Input

- `engagements/<customer>/06-architecture/architecture.md` (Risks & Assumptions, Open Questions sections).
- `engagements/<customer>/07-estimation/estimation-summary.md` (if available, for context on what's at stake).

## Step-by-Step Execution

1. List all architectural risks and open technical questions.
2. Rank them by (a) likelihood of materially changing scope/cost and (b) feasibility of validating quickly.
3. Select the top 1–3 candidates for PoC — avoid trying to validate everything.
4. For each selected PoC, define:
   - **Objective** — the specific technical question being answered.
   - **Success Criteria** — measurable, binary where possible (e.g. "p95 latency < 200ms for X requests").
   - **Out of Scope** — explicitly excluded work, to prevent scope creep.
   - **Timeline & Resourcing** — rough duration and skills needed.
5. Document the plan in `poc-plan.md`; after execution, document outcomes in `poc-results.md`.
6. If outcomes invalidate architecture/estimation assumptions, flag this back explicitly rather than quietly
   absorbing the change.

## Business Rules

- Every PoC must have explicit, measurable success criteria defined before work starts.
- PoC code/artifacts must never use real customer credentials or production data.
- Limit PoC scope tightly — a PoC proves a point, it is not a product increment.

## Output Format

`poc-plan.md`: Objective, Success Criteria, Out of Scope, Timeline, Resourcing, Linked Architecture Risk(s).
`poc-results.md`: Outcome, Evidence, Impact on Architecture/Estimate, Follow-up Actions.

## Quality Validation Checklist

- [ ] Each PoC has measurable success criteria defined up front.
- [ ] Out-of-scope items are explicitly listed.
- [ ] No real customer data/credentials are used.
- [ ] Outcomes that invalidate prior assumptions are flagged back to the Solution Architect/Technical Estimator.

## Example Usage

> Risk: "Unknown whether legacy ERP API can sustain required throughput."
> PoC: Load-test a mock integration against ERP's sandbox API; Success Criteria: sustain 50 req/s with <1% errors
> for 10 minutes.
