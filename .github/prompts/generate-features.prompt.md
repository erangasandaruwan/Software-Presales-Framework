---
agent: agent
description: Decompose an approved PRD into Features, Epics, and User Stories, prioritise them, and propose an MVP scope.
---

# Generate Features

Act as the `product-manager` agent and apply, in order, the `feature-mapping`, `feature-prioritisation`,
`tshirt-estimation`, and `mvp-identification` skills (see `skills/`).

## Inputs

- `engagements/${input:customer}/03-prd/prd.md` — must already be human-approved.
- `engagements/${input:customer}/02-requirements/requirements-baseline.md`

## Task

1. Decompose the PRD into Features → Epics → User Stories, each tagged with Requirement ID(s)
   (`skills/feature-mapping/SKILL.md`).
2. Score business priority per feature, independently of technical complexity/size
   (`skills/feature-prioritisation/SKILL.md`).
3. Apply T-shirt sizing (XS–XL) for early-stage scope indication (`skills/tshirt-estimation/SKILL.md`).
4. Propose an MVP scope with explicit rationale for every excluded feature
   (`skills/mvp-identification/SKILL.md`).
5. Follow all rules in [.github/copilot-instructions.md](../copilot-instructions.md).

## Expected Output

- `engagements/${input:customer}/04-feature-mapping/feature-mapping.xlsx`, based on
  [templates/feature-mapping-template.xlsx](../../templates/feature-mapping-template.xlsx).
- `engagements/${input:customer}/05-mvp/mvp-scope.md`.
- Stop and request human approval of the PRD-derived features (if not already approved) and the MVP scope
  (Checkpoint #3) before continuing to architecture.
