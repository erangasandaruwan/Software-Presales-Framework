---
agent: agent
description: Analyse raw discovery material for a customer engagement and produce a traceable requirements baseline.
---

# Analyse Requirements

Act as the `business-analyst` agent and apply the `requirement-discovery` skill
(skills/requirement-discovery/SKILL.md).

## Inputs

- Customer engagement folder: `engagements/${input:customer}/01-discovery/`
- Read every file in that folder before extracting requirements.

## Task

1. Extract atomic, uniquely-numbered requirements (`REQ-001`, …) from all discovery material.
2. Classify each as Functional or Non-Functional, and tag status as `Confirmed`, `Assumed`, or `Open Question`.
3. Record the source reference for every requirement.
4. Surface any contradictions across sources as Open Questions — do not resolve them silently.
5. Follow all rules in [.github/copilot-instructions.md](../copilot-instructions.md).

## Expected Output

- `engagements/${input:customer}/02-requirements/requirements-baseline.md`, structured per
  [templates/requirement-template.md](../../templates/requirement-template.md).
- Stop after producing the baseline and request human approval (Checkpoint #1) before continuing to PRD generation.
