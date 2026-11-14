---
name: requirement-discovery
description: Extracts atomic, traceable requirements from raw customer discovery material and classifies them as Confirmed, Assumed, or Open Question.
---

# Requirement Discovery Skill

## Purpose

Convert unstructured discovery material (meeting notes, transcripts, RFPs, emails) into a structured set of atomic,
uniquely identified requirements that downstream skills and agents can rely on as a single source of truth.

## When to Use

- At the start of a new customer engagement, once raw discovery material has been placed in
  `engagements/<customer>/01-discovery/`.
- Whenever new discovery material is added mid-engagement and the requirements baseline needs to be re-synced.

## Required Input

- One or more raw files under `engagements/<customer>/01-discovery/` (notes, transcripts, RFP documents, emails).
- The existing `requirements-baseline.md` (if this is an update rather than a first pass), to avoid renumbering.

## Step-by-Step Execution

1. Read every file in `01-discovery/` in full before extracting any requirement.
2. For each distinct idea/need/constraint found, draft **one atomic requirement** (do not bundle multiple needs
   into a single requirement).
3. Assign the next sequential Requirement ID (`REQ-001`, `REQ-002`, …); never reuse or renumber existing IDs.
4. Classify each requirement:
   - **Category**: Functional or Non-Functional (performance, security, availability, compliance, usability, etc.).
   - **Status**: `Confirmed` (directly quoted/paraphrased from source), `Assumed` (inferred, needs confirmation), or
     `Open Question` (information gap).
5. Record the **source reference** for every requirement (file name + section/quote/timestamp).
6. Compare requirements against each other; list any contradictions as `Open Questions` rather than resolving them
   silently.
7. Populate [`templates/requirement-template.md`](../../../templates/requirement-template.md) with the results.

## Business Rules

- Never invent requirements not traceable to source material or explicitly flagged as `Assumed` with rationale.
- One requirement = one testable idea. Split compound statements ("fast and secure") into separate requirements.
- Vague NFRs (e.g. "must be fast") must be flagged as `Open Question` until quantified.
- Conflicting statements across sources/stakeholders must be surfaced, not auto-resolved.

## Output Format

A Markdown table (per `requirement-template.md`) with columns: ID, Description, Category, Source, Status,
Priority (placeholder), Notes — plus an **Open Questions** section listing unresolved gaps/conflicts.

## Quality Validation Checklist

- [ ] Every requirement has a unique ID, source reference, category, and status.
- [ ] No requirement bundles more than one testable idea.
- [ ] No requirement is stated as fact without a traceable source or explicit `Assumed` tag.
- [ ] All contradictions found across sources are listed as Open Questions.
- [ ] Vague/unquantified NFRs are flagged, not silently accepted.

## Example Usage

> Input: a discovery call transcript stating "The portal needs to support SSO and handle about 500 concurrent
> users during peak season."
>
> Output:
> - `REQ-014` — System shall support Single Sign-On (SSO) authentication. | Functional | Confirmed | Source: call
>   transcript 2026-10-05, 00:12:40
> - `REQ-015` — System shall support at least 500 concurrent users during peak periods. | Non-Functional
>   (Performance) | Confirmed | Source: call transcript 2026-10-05, 00:13:05
> - Open Question: "Peak season" is undefined — clarify exact months/dates and expected growth trajectory.
