1. Confirm Gate 1 approved (use Wave method).
2. If the user is already in Codex and does not need external workers, recommend `wave-planner` instead.
3. Create `.planning/` if it does not exist.
4. Choose a clear feature-based filename and save the plan there.
5. Build and share one-line wave/agent preview.
6. Build full plan with section order A-G.
7. Tell the user where the plan file lives.
8. Confirm Gate 2 approved (execute plan).
9. Load and apply `acpx` skill before session execution.
10. For each wave in order:
- Start one named session per worker.
- Send worker prompt with full Wave Plan + worker assignment.
- Use `--prompt-retries` when transient failures are likely or already observed.
- Use `--suppress-reads` when cleaner logs help orchestration.
- Wait for worker handoff and completion marker.
- Validate ownership boundaries and test evidence.
- Close each finished worker session.
11. After all workers in wave are done, start next wave.
12. Run targeted checks first, then final verification checks.
13. Update docs (existing docs update or new docs for new feature).
14. Update the plan file status to `Completed` or `Blocked` and add final verification notes.
15. Share final merged summary and residual risks.
