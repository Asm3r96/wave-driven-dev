Read the approved Wave Plan below. Execute only your assigned task.

Agent: {AGENT_NAME}
Wave: {WAVE_ID}
Goal: {TASK_GOAL}

Allowed files/modules:
{FILES_ALLOWED}

Constraints:
- Do not edit files outside allowed list.
- If blocked by out-of-scope dependency, add a Dependency Note instead of editing extra files.
- Follow Decision Log conventions from the plan.
- Read full Wave Plan first to understand global context before editing.
- Keep changes scoped to your assigned task.

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
