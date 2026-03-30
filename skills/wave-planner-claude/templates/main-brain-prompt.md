Read the task context and determine if Wave method is justified.

Gate 1 (required):
- If the task is large, multi-step, and cross-stack, send a short reason:
  "I recommend using Wave method because <reason>. Do you agree?"
- Stop and wait for user accept/decline.

If user declines:
- Continue without this skill.

If user accepts:
- Build complete Wave-Driven plan.

Planning requirements:
- Include Vision with done criteria and explicit out-of-scope list.
- Include a Decision Log (naming, API shapes, error handling, logging, testing, formatting).
- Include Wave 0 contracts before implementation.
- Choose minimum wave count that avoids file conflicts.
- Group independent tasks in same wave; separate dependency-bound tasks into later waves.
- Keep worker tasks medium-sized.
- Include strict file ownership boundaries.
- Include Integration wave, Final verification wave, and Docs update step.
- Include one-line preview: one line per wave and one line per worker task.
- Include worker-ready prompts for each assigned worker.
- Read `templates/model-routing.md` and choose model per worker with fallback order.

Gate 2 (required):
- After full plan is ready, ask:
  "Plan is ready. Execute now?"
- Stop and wait for user accept/decline.

If user accepts Gate 2:
- Execute waves using Claude Code Agent tool.
- Launch one Agent per worker using `subagent_type: "general-purpose"`.
- All workers operate on the same working directory; ensure file ownership avoids conflicts.
- Use `model: "sonnet"` by default for workers; escalate to `opus` only with user approval.
- Launch all workers in the same wave as parallel Agent tool calls in a single message.
- Execute waves in strict order.
- Wait for all agents in wave to finish and validate handoffs before next wave.
- Track progress using TodoWrite tool.

Use this exact section order:
A) Vision
B) Decision Log
C) Contracts (Wave 0)
D) Waves
E) Integration + Final Verification + Docs
F) Worker Prompts
G) Execution Checklist
