---
name: prd-generation
description: Generates a structured Product Requirements Document from an approved requirements baseline, preserving full traceability to source requirements.
---

# PRD Generation Skill

## Purpose

Translate an approved, atomic requirements baseline into a cohesive Product Requirements Document (PRD) that
communicates product intent, scope, and constraints to both business and technical stakeholders.

## When to Use

- Immediately after the requirements baseline has received human approval (Checkpoint #1).
- When the requirements baseline is updated post-approval and the PRD needs to be re-synced (with changes clearly
  flagged).

## Required Input

- `engagements/<customer>/02-requirements/requirements-baseline.md` (human-approved).

## Step-by-Step Execution

1. Group related requirements into logical **capability areas** (e.g. "Authentication", "Reporting").
2. For each capability area, write a PRD section describing the **goal**, the **in-scope behavior**, and any
   **out-of-scope** notes — referencing the originating Requirement IDs.
3. Carry forward NFRs into a dedicated "Non-Functional Requirements" section, grouped by type (performance,
   security, compliance, availability, etc.), each referencing its Requirement ID.
4. Document assumptions and open questions inherited from the requirements baseline; do not resolve them silently.
5. Add a "Out of Scope" section listing explicitly excluded capabilities, if known at this stage.
6. Populate [`templates/prd-template.md`](../../../templates/prd-template.md).

## Business Rules

- Every PRD statement must trace to at least one Requirement ID; do not introduce new scope not present in the
  baseline (new ideas must be logged as `Assumed`/`Open Question`, not asserted as scope).
- Do not blend Confirmed and Assumed content without the status label carrying through from the baseline.
- Keep the PRD implementation-agnostic — architecture and technology choices belong to the Solution Architect.

## Output Format

Markdown document per `prd-template.md`: Executive Summary, Goals & Non-Goals, Capability Areas (each with
Requirement ID references), Non-Functional Requirements, Assumptions, Open Questions, Out of Scope.

## Quality Validation Checklist

- [ ] Every PRD section references originating Requirement ID(s).
- [ ] No new, un-traced requirements have been introduced.
- [ ] Confirmed vs. Assumed status is preserved from the baseline.
- [ ] NFRs are grouped and each is traceable.
- [ ] Open Questions carried forward (not silently dropped).

## Example Usage

> Input: `REQ-014` (SSO), `REQ-015` (500 concurrent users).
>
> Output PRD excerpt:
> ### Authentication (REQ-014)
> Goal: Allow enterprise users to authenticate via their existing identity provider.
> In Scope: SAML 2.0 / OIDC-based SSO integration.
> ### Non-Functional Requirements
> Performance (REQ-015): System shall sustain 500 concurrent users during peak periods *(Open Question: peak
> season dates undefined)*.
