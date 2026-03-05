1. Confirm Gate 1 approved (use Wave method).
2. Build and share one-line wave/agent preview.
3. Build full plan with section order A-G.
4. Confirm Gate 2 approved (execute plan).
5. Load and apply `acpx` skill before session execution.
6. For each wave in order:
- Start one named session per worker.
- Send worker prompt with full Wave Plan + worker assignment.
- Wait for worker handoff and completion marker.
- Validate ownership boundaries and test evidence.
- Close each finished worker session.
7. After all workers in wave are done, start next wave.
8. Run integration checks, then final verification checks.
9. Update docs (existing docs update or new docs for new feature).
10. Share final merged summary and residual risks.
