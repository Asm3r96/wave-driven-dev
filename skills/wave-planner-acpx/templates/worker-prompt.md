Read the original approved Wave Plan file first for full context. Then execute only your assigned task.

Original plan file:
{PLAN_FILE}

Agent: {AGENT_NAME}
Wave: {WAVE_ID}
Goal: {TASK_GOAL}

Allowed files/modules:
{FILES_ALLOWED}

Constraints:
- Do not edit files outside allowed list.
- If blocked by out-of-scope dependency, add a Dependency Note instead of editing extra files.
- Follow Decision Log conventions from the plan.
- Read the original plan file first to understand the full picture before editing.
- Keep changes scoped to your assigned task.
- You are not alone in the codebase. Do not revert other workers' changes.

Verification requirement:
{TEST_REQUIREMENT}

Mandatory test behavior:
- If tests exist for touched behavior, run them.
- If logic changed and tests are outdated, update tests first, then run them.
- If feature is new and no tests exist, add tests, then run them.
- Report exact commands and expected/actual results.

Mandatory plan log behavior:
- Add a concise execution log entry that can be appended to the shared main plan log.
- Include files changed and tests added/updated/run.
- Return one clean final handoff suitable for appending to the original plan file.

Return exactly this handoff format:
1) Summary
2) Files changed
3) Patch/diffs
4) How to test (commands + expected results)
5) Risks/TODOs/Dependency Notes
6) Main plan log entry
7) Completion marker: WAVE {WAVE_ID} / {AGENT_NAME} DONE

Wave Plan:
{WAVE_PLAN}
