# Wave Execution Runbook

## Inputs
- Approved Wave Plan
- Worker prompts
- Test commands

## Per-wave loop
1. Start sessions for all non-conflicting workers.
2. Send worker prompts.
3. Wait for completion markers.
4. Validate handoff format.
5. Merge in planned order.
6. Run wave-level checks.
7. Record Decision Log updates if any.

## Integration wave
- Merge all remaining work
- Fix only integration issues
- Re-run integration test matrix

## Final verification wave
- Run full test/lint/typecheck
- Execute smoke checklist
- Prepare release notes/changelog summary
