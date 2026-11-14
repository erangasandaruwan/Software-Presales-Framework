---
name: mvp-identification
description: Selects a minimum viable product scope from the full feature set, balancing business priority, size, and dependencies, with explicit rationale for exclusions.
---

# MVP Identification Skill

## Purpose

Propose a Minimum Viable Product (MVP) scope — the smallest set of features that deliver standalone customer
value — from the full feature list, with transparent rationale for what is included and excluded.

## When to Use

- After features have been mapped and business-priority/T-shirt sizing has been applied.
- When re-scoping an MVP due to budget, timeline, or new requirement changes.

## Required Input

- `engagements/<customer>/04-feature-mapping/feature-mapping.xlsx` with Priority and T-Shirt Size populated.

## Step-by-Step Execution

1. Sort features by business priority (highest first), then consider dependencies between features.
2. Identify **hard dependencies** (Feature B cannot function without Feature A) and keep dependent chains intact.
3. Select the smallest set of high-priority features that forms a coherent, demonstrable product for the customer.
4. For every feature **excluded** from MVP, write one line of rationale (e.g. low priority, high size, nice-to-have).
5. Validate the proposed MVP against known constraints (timeline/budget hints from discovery, if any — never
   invented).
6. Write the MVP scope document using a simple Markdown structure (Included / Excluded / Rationale / Open
   Questions).

## Business Rules

- MVP selection is driven by business priority and dependency feasibility — technical complexity informs risk
  notes but does not override priority-driven selection.
- Every exclusion must have a stated rationale; "excluded" without rationale is not acceptable.
- Do not assume a budget or timeline ceiling that was not confirmed by the customer; if used as a constraint, tag
  it `Assumed` and flag for confirmation.

## Output Format

Markdown document (`engagements/<customer>/05-mvp/mvp-scope.md`): Included Features (with IDs), Excluded Features
(with rationale), Dependency Notes, Assumptions, Open Questions.

## Quality Validation Checklist

- [ ] Every included feature has a stated priority justifying inclusion.
- [ ] Every excluded feature has an explicit rationale.
- [ ] Hard dependency chains are not broken by partial inclusion.
- [ ] Any budget/timeline constraint used is tagged Confirmed or Assumed appropriately.

## Example Usage

> Included: FEAT-001 (Login), FEAT-003 (SSO) — both high priority, FEAT-003 depends on FEAT-001.
> Excluded: FEAT-009 (Advanced analytics dashboard) — Medium priority, Large T-shirt size, deferred to Phase 2.
