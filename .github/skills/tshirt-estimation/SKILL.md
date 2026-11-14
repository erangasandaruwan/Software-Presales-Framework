---
name: tshirt-estimation
description: Applies early-stage, low-confidence T-shirt sizing (XS/S/M/L/XL) to features before detailed design exists.
---

# T-Shirt Estimation Skill

## Purpose

Provide a fast, low-confidence relative sizing of features (XS, S, M, L, XL) early in the pre-sales process, before
architecture detail exists, to support MVP scoping discussions.

## When to Use

- During feature mapping / MVP identification, before the Solution Architect has produced a detailed architecture.
- Must precede PERT estimation — do not skip straight to PERT without this stage unless the engagement explicitly
  starts at a detailed design stage.

## Required Input

- `engagements/<customer>/04-feature-mapping/feature-mapping.xlsx` (Features/Stories populated).

## Step-by-Step Execution

1. For each feature/story, compare relative scope/complexity against a reference feature the team has delivered
   before (if known) or against other features in the same list.
2. Assign a size: `XS` (trivial, <1 day equivalent), `S`, `M`, `L`, `XL` (large, needs decomposition before it can
   be delivered as-is).
3. Record one-line rationale per size (e.g. "M — standard CRUD screen with one integration").
4. Flag any `XL` feature as a candidate for further decomposition into smaller stories before MVP/estimation.
5. Populate the T-Shirt Size column in `feature-mapping.xlsx`.

## Business Rules

- T-shirt sizes are relative and low-confidence by design — never present them as effort/cost figures to the
  customer.
- Do not let business priority influence the size given; size reflects scope/complexity only.
- `XL` items should be flagged, not estimated as a black box — recommend decomposition.

## Output Format

Updated `feature-mapping.xlsx` T-Shirt Size column (XS/S/M/L/XL) with rationale notes.

## Quality Validation Checklist

- [ ] Every feature/story has a size and one-line rationale.
- [ ] No `XL` item proceeds to MVP/estimation without a decomposition recommendation.
- [ ] Sizes are not blended with or derived from priority scores.

## Example Usage

> FEAT-003 (SSO) — Size: M. Rationale: standard OIDC integration, comparable to past SSO work, one external
> dependency (customer's IdP).
