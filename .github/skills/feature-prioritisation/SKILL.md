---
name: feature-prioritisation
description: Scores business priority for each feature independently of technical complexity, using a transparent value/urgency-based method.
---

# Feature Prioritisation Skill

## Purpose

Assign a **business priority** score to each feature based on customer value and urgency, kept strictly independent
from technical complexity/effort (which is scored separately by the Solution Architect / Technical Estimator).

## When to Use

- After features are mapped (`feature-mapping`), before MVP identification.
- When priorities need re-validation after customer feedback or new discovery input.

## Required Input

- `engagements/<customer>/04-feature-mapping/feature-mapping.xlsx` (Feature/Story rows populated).
- Any customer statements on urgency/value from discovery material (for traceable justification).

## Step-by-Step Execution

1. For each feature, assess **business value** (impact on customer's goals, revenue, risk reduction) using evidence
   from discovery material — never guess value without a cited rationale.
2. Assess **urgency** (customer-stated deadlines, dependencies on external events) similarly sourced.
3. Combine into a single priority tier: `Must Have`, `Should Have`, `Could Have`, `Won't Have` (MoSCoW), or a 1–5
   numeric score — pick one scale and apply it consistently within the engagement.
4. Record a one-line justification per feature citing the discovery source or PRD section.
5. Populate the Priority column in `feature-mapping.xlsx` — do not touch the Technical Complexity column.

## Business Rules

- Priority must never be inferred from ease/difficulty of implementation — that is a separate axis.
- Every priority score requires a citation (discovery quote, PRD reference, or explicit `Assumed` tag with
  rationale if the customer hasn't stated a preference).
- Use one scale consistently per engagement; do not mix MoSCoW and numeric scales within the same feature list.

## Output Format

Updated `feature-mapping.xlsx` Priority column (MoSCoW or 1–5), plus a short justification note per row.

## Quality Validation Checklist

- [ ] Every feature has a priority score and a cited justification.
- [ ] Priority scale is used consistently across all features in the engagement.
- [ ] No priority score was influenced by technical complexity/effort.
- [ ] Assumed priorities (no explicit customer statement) are flagged as such.

## Example Usage

> FEAT-003 (SSO) — Priority: Must Have. Justification: customer stated "all enterprise clients require SSO to
> sign a contract" (discovery call, 2026-10-05).
