# Global Copilot Instructions — Software Pre-Sales Framework

Repository-wide principles that apply automatically to every chat request in this workspace, and must not be
contradicted by any custom agent, skill, or prompt file in this repository. Where a conflict exists, these global
instructions take precedence.

# Global Principles for AI-Assisted Software Pre-Sales

These instructions apply to **every** custom agent, skill, and prompt file in this repository. Agents and skills
must not contradict these principles. Where a conflict exists, these global instructions take precedence.

## 1. Source of Truth

- Customer-provided requirements (meeting notes, RFPs, emails, transcripts, documents placed under an engagement's
  `01-discovery/` or `02-requirements/` folder) are the **primary source of truth**.
- **Never invent, assume, or fabricate customer requirements, constraints, budgets, or timelines.** If information is
  not present in the source material, it must be explicitly flagged as **missing information**, not filled in.
- When source material is ambiguous or silent, generate a clearly labelled **Assumption** and route it for human
  confirmation rather than treating it as fact.

## 2. Confirmed vs. Assumed

- Every requirement, feature, or estimate produced by an agent must be tagged with a status:
  - `Confirmed` — directly traceable to a customer-provided source.
  - `Assumed` — inferred by the agent/skill, pending customer or internal confirmation.
  - `Open Question` — information gap that must be resolved before proceeding.
- Documents must never blend these categories without clear labels (e.g. a table column, a badge, or a heading).

## 3. Traceability

- Maintain end-to-end traceability: **Requirement → Feature → User Story/Epic → Estimate → Proposal line item**.
- Every feature or user story must reference the requirement ID(s) it originates from.
- Every estimate line must reference the feature/user story it estimates.
- When generating new documents, carry forward IDs from upstream documents rather than renumbering from scratch.

## 4. Gaps and Conflicts

- Actively identify missing information needed to proceed (e.g. unclear NFRs, undefined integrations, absent
  volumetrics) and list them as **Open Questions**.
- Actively identify conflicting requirements (e.g. contradictory statements across documents or stakeholders) and
  surface them explicitly rather than silently resolving them.

## 5. Priority vs. Complexity

- **Business priority** (value to the customer, urgency, strategic importance) and **technical complexity**
  (engineering effort, risk, dependencies) are separate dimensions and must be scored independently.
- Never let perceived technical ease/difficulty silently influence the stated business priority, and vice versa.

## 6. Estimation Discipline

- Use **T-shirt sizing** (XS/S/M/L/XL) for early-stage, low-confidence estimation (e.g. during feature mapping and
  MVP scoping), before a detailed design exists.
- Use **PERT (Program Evaluation and Review Technique)** for effort estimation once features/stories are reasonably
  well understood: `Expected Effort = (Optimistic + 4 × Most Likely + Pessimistic) / 6`.
- Do not skip T-shirt sizing and jump straight to PERT unless the engagement explicitly starts at a detailed stage.

## 7. Commercial Guardrails

- **Never make unsupported cost or timeline commitments.** All costs/timelines in proposals must be derived from the
  estimation templates and marked as **indicative** unless explicitly approved by a human reviewer.
- Do not quote fixed prices or delivery dates without a human approval checkpoint having been passed.

## 8. Security and Confidentiality

- Treat all customer data (names, business details, financials, source documents) as confidential.
- Do not copy customer data outside the relevant `engagements/<customer>/` folder.
- Do not include secrets, credentials, or personal data in generated templates or examples.
- Redact or generalize sensitive details when producing reusable examples in `skills/` or `templates/`.

## 9. Human Approval Checkpoints

The following decisions **require explicit human approval** before the workflow may proceed:

1. Finalized requirements baseline (end of Requirement Discovery).
2. Approved PRD (end of PRD Generation).
3. Finalized MVP scope (end of MVP Identification).
4. Approved solution architecture (end of Solution Architecture).
5. Final effort estimate and commercial figures (end of Estimation).
6. Proposal content and pricing before sending to the customer (end of Proposal Generation).

Agents must pause and request human sign-off at these checkpoints instead of auto-proceeding.

## 10. Working Conventions

- All generated artifacts for a customer live under `engagements/<customer-name>/<NN-stage>/`.
- Agents should reuse `templates/` and `skills/` rather than re-deriving format conventions ad hoc.
- Use relative paths when referencing other files in this repository.
- Keep generated documents concise, structured, and reviewable — prefer tables and headings over long prose.
