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
- If the user is already in Codex and does not need external workers, recommend switching to `wave-planner` instead.
- Create `.planning/` if it does not exist.
- Choose a clear feature-based filename and save the plan there.
- Choose minimum wave count that avoids file conflicts.
- Group independent tasks in same wave; separate dependency-bound tasks into later waves.
- Keep worker tasks medium-sized.
- Include strict file ownership boundaries.
- Include Integration wave, Final verification wave, and Docs update step.
- Include one-line preview: one line per wave and one line per worker task.
- Include worker-ready prompts for each assigned worker.
- Read `templates/model-routing.md` and choose model per worker with fallback order.
- Save the full plan to the plan file by default; do not dump the full plan in chat unless the user asks.

Gate 2 (required):
- After full plan is ready, ask:
  "Plan is ready. Execute now?"
- Stop and wait for user accept/decline.

If user accepts Gate 2:
- Load and use `acpx` skill.
- Execute waves in strict order.
- Run workers in parallel inside each wave.
- Use `--prompt-retries` when transient failures are likely or already observed.
- Use `--suppress-reads` when cleaner logs help orchestration.
- Wait for all workers in wave to finish and validate handoffs before next wave.
- Close worker sessions after each worker is done.

Use this exact section order:
A) Vision
B) Decision Log
C) Contracts (Wave 0)
D) Waves
E) Integration + Final Verification + Docs
F) Worker Prompts
G) Execution Checklist
