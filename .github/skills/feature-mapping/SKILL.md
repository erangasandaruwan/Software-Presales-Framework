---
name: feature-mapping
description: Decomposes an approved PRD into Features, Epics, and User Stories, each traceable back to source requirements.
---

# Feature Mapping Skill

## Purpose

Break down PRD capability areas into concrete, independently sizeable Features, Epics, and User Stories, preserving
full traceability from each story back to its originating requirement(s).

## When to Use

- After the PRD is approved (Checkpoint #2), before MVP identification and prioritisation.
- When PRD scope changes and the feature breakdown needs to be regenerated or extended.

## Required Input

- `engagements/<customer>/03-prd/prd.md` (approved).
- `engagements/<customer>/02-requirements/requirements-baseline.md` (for Requirement ID references).

## Step-by-Step Execution

1. For each PRD capability area, identify one or more **Features**.
2. For each Feature, decompose into **Epics** (if large) and then **User Stories** in the standard form:
   "As a `<role>`, I want `<capability>`, so that `<benefit>`."
3. Tag every Feature/Epic/Story with the Requirement ID(s) it originates from.
4. Assign a Feature ID (`FEAT-001`, …) and Story ID (`US-001`, …), sequential and never reused.
5. Populate [`templates/feature-mapping-template.xlsx`](../../../templates/feature-mapping-template.xlsx) — one row
   per Feature/Story, with columns for IDs, description, requirement references, and placeholders for priority,
   T-shirt size, and technical complexity (filled in by later skills).

## Business Rules

- Every Feature/Story must reference at least one Requirement ID — no orphan features.
- Do not pre-fill business priority or technical complexity here; those are scored by dedicated skills.
- Keep stories small enough to be independently estimable; split stories that bundle multiple behaviors.

## Output Format

An Excel workbook (`feature-mapping-template.xlsx`) with a `Features` worksheet: Feature ID, Epic, User Story ID,
Description, Requirement ID(s), Priority (blank), T-Shirt Size (blank), Technical Complexity (blank), Notes.

## Quality Validation Checklist

- [ ] Every Feature/Story has a unique ID and at least one Requirement ID reference.
- [ ] Stories follow the "As a / I want / so that" structure.
- [ ] No story bundles unrelated behaviors.
- [ ] Priority/complexity columns are left blank for later skills to populate.

## Example Usage

> Input PRD section: "Authentication (REQ-014)".
>
> Output rows:
> - `FEAT-003` / `US-011` — "As an enterprise employee, I want to log in via my company's SSO, so that I don't
>   need a separate password." — Requirement Ref: REQ-014.
