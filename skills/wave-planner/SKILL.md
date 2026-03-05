---
name: wave-planner
description: Build a contract-first Wave Plan for large changes with parallel agents, ownership boundaries, and explicit integration/final verification waves.
metadata:
  short-description: Generate Wave 0 contracts and parallel implementation waves
---

# Wave Planner

Create a full Wave-Driven Development plan before implementation starts.

## Objective

Produce a plan with:
- Vision and scope boundaries
- Decision Log
- Wave 0 contracts
- Wave 1..N parallel implementation waves
- Integration wave
- Final verification wave
- Ready-to-send worker prompts

## Workflow

1. Clarify acceptance criteria and out-of-scope items.
2. Create a Decision Log (naming, API shape, error model, logging, tests, style constraints).
3. Define Wave 0 contracts:
- types/interfaces/schemas
- module/file boundaries
- API/route shapes
- event names/constants
- feature flags/migrations if needed
4. Split implementation into parallel waves where each worker has explicit file ownership.
5. Add Integration wave with merge order and integration-only fixes.
6. Add Final verification wave with full test matrix and smoke checklist.
7. Generate worker prompts with constraints and required handoff format.

## Global Rules

- Ownership rule: workers edit only assigned files.
- Dependency rule: if outside scope is needed, return a Dependency Note instead of editing.
- Consistency rule: follow existing repo patterns; do not invent new architecture unless requested.
- Verifiability rule: each worker includes at least one concrete verification method.

## Mandatory Worker Handoff Format

1. Summary (1-3 lines)
2. Files changed (exact list)
3. Patch/diffs (or exact edits)
4. How to test (commands + expected result)
5. Risks/TODOs/Dependency Notes

## Output Contract

Always output the final plan using this section order:
- A) Vision
- B) Decision Log
- C) Contracts (Wave 0)
- D) Waves (1..N with agents)
- E) Integration + Final Verification
- F) Worker prompts

Use templates from `templates/` when helpful.
