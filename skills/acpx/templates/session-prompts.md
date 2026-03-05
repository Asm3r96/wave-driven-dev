# Session prompt template

You are {AGENT_NAME} for {WAVE_ID}.
Read the assigned task and follow constraints exactly.

Task:
{TASK_PROMPT}

Constraints:
- Edit only allowed files: {FILES_ALLOWED}
- Follow the Decision Log and contracts.
- Do not refactor outside scope.
- If blocked, include Dependency Note.

Return this exact format:
1. Summary
2. Files changed
3. Patch/diffs
4. How to test
5. Risks/TODOs/Dependency Notes

Finish with exact marker:
WAVE {WAVE_ID} / {AGENT_NAME} DONE
