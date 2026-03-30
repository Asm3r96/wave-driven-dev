1. Confirm Gate 1 approved (use Wave method).
2. Create `.planning/` if it does not exist.
3. Choose a clear feature-based filename and save the plan there.
4. Build and share one-line wave/agent preview.
5. Build full plan with section order A-G.
6. Save the full plan to the plan file; do not dump the full plan in chat unless the user asks.
7. Tell the user where the plan file lives.
8. Confirm Gate 2 approved (execute plan).
9. For each wave in order:
- Launch one Agent per worker using the Claude Code Agent tool.
- Use `model: "sonnet"` by default; use `opus` only if user approved an exception.
- All workers operate on the same working directory.
- Use `subagent_type: "general-purpose"` for all workers.
- Include the full plan context in each worker's prompt so agents have the complete picture.
- Launch all agents in the same wave as parallel Agent calls in a single message.
- Wait for all agent results and validate handoffs.
- Validate ownership boundaries and test evidence.
- Collect handoffs and append them into the original plan file.
- Remove duplicate worker handoff entries if needed and keep one clean final entry.
10. After all workers in wave are done, start next wave.
11. Run targeted checks first, then broader final verification checks.
12. Update docs (existing docs update or new docs for new feature).
13. If `docs/STATUS.md` exists, update it so completed work and remaining open work are accurate.
14. Update the plan file status to `Completed` or `Blocked` and add final verification notes.
15. Before committing, inspect git status and stage only the files that belong to the planned task.
16. If `docs/STATUS.md` exists, re-check it before closing out and ensure it matches the final shipped result.
17. Share a short merged summary with plan path, checks passed, and residual risks or out-of-scope failures.
