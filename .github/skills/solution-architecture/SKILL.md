---
name: solution-architecture
description: Produces a component-level technical architecture satisfying the approved MVP scope and requirements, covering functional and non-functional needs.
---

# Solution Architecture Skill

## Purpose

Design a technical solution architecture — components, integrations, data flows, and deployment topology — that
satisfies the approved MVP scope and the requirements baseline, including non-functional requirements.

## When to Use

- After the MVP scope is human-approved (Checkpoint #3).
- When architecture needs revisiting due to new/changed requirements or PoC findings.

## Required Input

- `engagements/<customer>/02-requirements/requirements-baseline.md`
- `engagements/<customer>/03-prd/prd.md`
- `engagements/<customer>/05-mvp/mvp-scope.md` (approved)

## Step-by-Step Execution

1. Map each MVP feature to the system component(s) that will implement it.
2. Define integration points with existing customer systems mentioned in discovery (never invent integrations not
   mentioned or requested).
3. Address each Non-Functional Requirement (performance, security, availability, compliance) with a specific
   architectural mechanism (e.g. caching strategy, auth mechanism, redundancy approach).
4. Produce a high-level component diagram (described in text/Mermaid) and a deployment topology outline.
5. List architectural risks, assumptions, and open technical questions.
6. Populate [`templates/architecture-template.md`](../../../templates/architecture-template.md).

## Business Rules

- Every architectural decision tied to cost/effort must cite the requirement(s)/NFR(s) driving it.
- Do not select technologies unsupported by stated requirements or customer constraints — offer them as
  recommendations tagged `Assumed`, not settled decisions, unless the user confirms.
- Keep business priority out of this skill's scope — this skill scores/describes technical complexity and risk
  only.

## Output Format

Markdown document per `architecture-template.md`: Architecture Overview (with Mermaid component diagram),
Component Responsibilities, Integration Points, NFR Coverage Table, Deployment Topology, Risks & Assumptions, Open
Questions.

## Quality Validation Checklist

- [ ] Every MVP feature maps to at least one architecture component.
- [ ] Every NFR has an explicit architectural mechanism addressing it.
- [ ] No invented integrations/technologies without traceable justification.
- [ ] Risks, assumptions, and open questions are explicitly listed.

## Example Usage

> FEAT-003 (SSO) maps to "Identity & Access component", integrating with customer's existing Azure AD via OIDC,
> addressing REQ-014. Risk noted: customer's Azure AD tenant configuration unknown — Open Question.
