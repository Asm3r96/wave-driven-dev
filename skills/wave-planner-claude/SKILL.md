---
name: wave-planner-claude
description: Plan and execute large multi-step, multi-stack changes with contract-first waves, parallel worker ownership, user approval gates, ordered integration, and final verification/docs updates using Claude Code Agent subagents. Use only when the task spans multiple areas (for example frontend, backend, tests, errors, docs) or has dependency-heavy sequencing.
---

# Wave Planner (Claude Code)

Create and run a Wave-Driven Development plan for large, cross-stack tasks using Claude Code's native Agent tool.

## Objective

Produce:
- Vision and scope boundaries
- Decision Log
- Wave 0 contracts
- Wave 1..N parallel implementation waves
- Integration wave
- Final verification wave
- Documentation update step
- Ready-to-send worker prompts and execution checklist

## Workflow

1. Decide whether to use this skill:
- Use only if work is large, multi-step, and touches multiple parts/stacks.
- If not large enough, do not use this skill.
2. Ask for Gate 1 user approval before planning:
- Send a short reason: "I recommend Wave method because <short reason>. Do you agree?"
- Stop until user accepts or declines.
3. If accepted, draft the plan:
- Clarify done criteria and out-of-scope.
- Build Decision Log (naming, API shape, error model, logging, tests, style constraints).
- Define Wave 0 contracts first (types/interfaces/schemas, boundaries, API shapes, constants, flags/migrations).
- Because worker agents use the `sonnet` model by default, make the plan clear and concrete so agents can execute reliably without guessing.
- Save the plan by default inside `.planning/`; create the folder if it does not exist.
- Use a clear feature-based filename for the plan.
4. Choose wave and agent count with balancing rules:
- Prefer 1-2 waves unless more waves are clearly needed to avoid conflicts or sequencing problems.
- Use the minimum number of waves that still avoids conflicts.
- Group independent tasks into the same wave.
- Move dependency-bound tasks to later waves.
- Keep each worker task medium-sized (not tiny and not overloaded).
- Ensure each worker has explicit file/module ownership.
5. Produce a one-line execution preview before full detail:
- One line per wave.
- One line per worker with task summary.
6. Produce the full plan with complete shared context:
- Include full vision and all waves so each worker sees global intent.
- Include worker-specific goals, files, constraints, and verification.
- Include explicit wave order for execution (Wave 0, then Wave 1..N, then Integration, then Final Verification, then Docs).
- Make each worker prompt highly specific: exact ownership, exact files/modules, exact handoff format, exact verification steps, and any important non-goals.
- By default, save the full plan to the plan file and do not dump the full plan in chat unless the user explicitly asks.
7. Ask for Gate 2 user approval before execution:
- "Plan is ready. Execute now?"
- Stop until user accepts or declines.
8. If accepted, execute with Claude Code Agent subagents:
- Spawn one named Agent per worker in the current wave using the Claude Code `Agent` tool.
- Use the `sonnet` model override for worker agents by default.
- Use `opus` for unusually complex workers, only if the user approves.
- The main agent (you) controls the subagents, assigns ownership, monitors progress, validates handoffs, and decides when a wave is complete.
- Launch all agents within a wave in parallel (multiple Agent tool calls in a single message).
- Execute waves sequentially — wait for all agents in the current wave to finish and validate handoffs before starting the next wave.
- Track progress using the TodoWrite tool, marking each worker/wave as pending, in_progress, or completed.
9. After all waves:
- Main agent reviews merged result and runs verification tests.
- Main agent updates existing docs if needed, or adds new docs for new features.
- Follow existing documentation format and conventions.
- Main agent updates the original plan file status to `Completed` or `Blocked`.
- Main agent adds final verification notes to the original plan file.
- If a `docs/STATUS.md` exists in the repo, update it so completed work and remaining open work stay accurate.

## Global Rules

- Gating rule: planning and execution require explicit user approvals (Gate 1 and Gate 2).
- Ownership rule: workers edit only assigned files.
- Dependency rule: if outside scope is needed, return a Dependency Note instead of editing.
- Consistency rule: follow existing repo patterns; do not invent new architecture unless requested.
- Verifiability rule: each worker includes at least one concrete verification method.
- Ordering rule: wave order is strict; do not start next wave early.
- Agent rule: one named Agent subagent per worker.
- Planning quality rule: the main plan must be detailed, concrete, and unambiguous enough that workers do not need to invent missing structure.
- Plan-location rule: save plans in `.planning/` by default and create the folder if needed.
- Worker-context rule: every worker prompt must include the full plan context so the agent has the complete picture before editing.
- Handoff rule: every worker must produce its handoff in the format specified; the main agent collects and appends handoffs into the original plan file.
- Deduplication rule: if a worker reports more than once, keep one clean final handoff entry in the plan file.
- Commit-scope rule: before committing, inspect git status and commit only the files that belong to the planned task.
- Verification-scope rule: run targeted checks first, then broader checks; report unrelated pre-existing failures clearly as outside the feature scope.
- Status-tracking rule: if `docs/STATUS.md` exists, update it as part of the task closeout so the project status reflects what was completed and what remains open.
- Docs rule: docs update is mandatory in final step (update existing docs or add new).
- Progress rule: use TodoWrite to track wave/worker progress throughout execution.

## Claude Code Agent Configuration

Use Claude Code's built-in Agent tool for execution.

Rules:
- Default all worker agents to the `sonnet` model for execution.
- The main agent (you) remains responsible for planning, orchestration, integration, and final verification.
- Prefer a very strong plan, strict ownership, and clear contracts over increasing model size.
- Workers perform best when instructions are explicit, scoped, and testable; plan accordingly.
- If a task is unusually complex and `sonnet` is clearly insufficient, pause and ask the user before using `opus`.
- Do not use per-task model routing by default; prefer `sonnet` unless the user approves an exception.
- Launch all agents in a wave as parallel Agent tool calls in a single message for maximum concurrency.

## Agent Tool Usage Pattern

For each worker in a wave, use:

```
Agent tool call:
  description: "Wave {N} - {worker-name}"
  prompt: <full worker prompt from templates/worker-prompt.md>
  model: "sonnet"           (or "opus" if approved)
  subagent_type: "general-purpose"
```

Launch all workers in the same wave as parallel Agent calls in a single message.

## Mandatory Worker Handoff Format

1. Summary (1-3 lines)
2. Files changed (exact list)
3. Patch/diffs (or exact edits)
4. How to test (commands + expected result)
5. Risks/TODOs/Dependency Notes
6. Main plan log entry (what to append to shared execution log)
7. Completion marker: `WAVE {WAVE_ID} / {AGENT_NAME} DONE`

## Output Contract

Always output the final plan using this section order:
- A) Vision
- B) Decision Log
- C) Contracts (Wave 0)
- D) Waves (1..N with agents)
- E) Integration + Final Verification + Docs
- F) Worker prompts
- G) Execution checklist (Agent subagents + wave order)

Use templates from `templates/` when helpful.

## Final Response Contract

After execution, keep the user-facing summary short by default and include:
- what was implemented
- where the plan file lives
- what tests/checks passed
- what is still failing, blocked, or outside scope
