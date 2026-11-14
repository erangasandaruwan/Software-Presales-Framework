---
agent: agent
description: Produce a solution architecture document for the approved MVP scope and requirements baseline.
---

# Generate Architecture

Act as the `solution-architect` agent and apply the `solution-architecture` skill
(skills/solution-architecture/SKILL.md).

## Inputs

- `engagements/${input:customer}/05-mvp/mvp-scope.md` — must already be human-approved. If not approved, stop.
- `engagements/${input:customer}/03-prd/prd.md`
- `engagements/${input:customer}/02-requirements/requirements-baseline.md`

## Task

1. Map each MVP feature to the architecture component(s) that implement it.
2. Address every Non-Functional Requirement with a specific architectural mechanism.
3. Produce a component diagram (Mermaid), integration points, and deployment topology outline.
4. List architectural risks, assumptions, and open technical questions.
5. Score technical complexity per feature in the feature-mapping sheet, independent of business priority.
6. Follow all rules in [.github/copilot-instructions.md](../copilot-instructions.md).

## Expected Output

- `engagements/${input:customer}/06-architecture/architecture.md`, based on
  [templates/architecture-template.md](../../templates/architecture-template.md).
- Updated `engagements/${input:customer}/04-feature-mapping/feature-mapping.xlsx` with technical complexity scores.
- Stop after producing the architecture and request human approval (Checkpoint #4) before continuing to estimation.
