# wave-driven-dev

Wave-Driven Development for coding agents: plan once, execute in waves, parallelize safely, and integrate with control.

Current version: `v0.2.0`

![wave-driven-dev banner](./assets/wave-driven-dev-banner.png)

## Recommended

Use `wave-planner` with Codex first.

Codex subagents are now good enough that this should be the default path for most users:
- easier to track worker activity in the Codex app and CLI
- easier to steer, stop, and inspect running subagents
- simpler than external orchestration when you are already working in Codex

Docs:
- [Codex subagents](https://developers.openai.com/codex/subagents)

Use `wave-planner-claude` when you want the same Wave method but inside Claude Code.

Use `wave-planner-acpx` only when you explicitly want external workers through `acpx`, such as mixed-agent runs across Codex, Claude Code, Gemini, or other ACP-compatible tools.

## Skills

- `wave-planner`
  - Codex-first Wave skill
  - Uses Codex subagents for execution
- `wave-planner-claude`
  - Claude Code Wave skill
  - Uses Claude Code Agent subagents for execution
- `wave-planner-acpx`
  - Wave skill for `acpx`-based execution
  - Use when you want cross-CLI or cross-provider workers
- `acpx`
  - Lower-level `acpx` reference skill
  - Covers CLI usage, sessions, and orchestration details

## Install

Install the skills:

```bash
npx skills add https://github.com/Asm3r96/wave-driven-dev
```

Install `acpx` only if you plan to use `wave-planner-acpx`:

```bash
npm install -g acpx@latest
```

## Quick Start

### Codex path

1. Use `wave-planner`.
2. Approve Gate 1.
3. Review the generated Wave Plan.
4. Approve Gate 2.
5. Let Codex run the wave with subagents, integrate, and verify.

### `acpx` path

1. Install `acpx`.
2. Use `wave-planner-acpx`.
3. Approve Gate 1.
4. Review the generated Wave Plan.
5. Approve Gate 2.
6. Execute the waves through `acpx`.

### Claude Code path

1. Use `wave-planner-claude`.
2. Approve Gate 1.
3. Review the generated Wave Plan.
4. Approve Gate 2.
5. Let Claude Code run the wave with Agent subagents, integrate, and verify.

<details>
<summary>Why this method exists</summary>

Traditional single-agent sessions often lead to:

- overloaded context windows
- slower iteration
- weak separation of concerns
- more merge conflicts when tasks are broad

Wave-Driven Development changes that by using:

- one Main Brain for planning and integration
- Wave 0 contracts before implementation
- parallel workers inside each wave
- strict ownership boundaries
- ordered integration and final verification

</details>

<details>
<summary>Why Codex is the recommended default now</summary>

OpenAI’s Codex subagents can spawn specialized agents in parallel and collect the results back into one response. Current Codex releases enable subagent workflows by default, and subagent activity is surfaced in the Codex app and CLI.

That makes the Codex-native version of Wave-Driven Dev the simplest and most reliable default when you are already inside Codex.

</details>

<details>
<summary>When to use <code>wave-planner-acpx</code> instead</summary>

Use the `acpx` version when:

- you want workers from different agent CLIs
- you want model/provider routing outside Codex
- you want session-based external orchestration
- you need an ACP-based workflow across tools

</details>

<details>
<summary>Which skill should I pick?</summary>

- Use `wave-planner` if you are working only in Codex.
- Use `wave-planner-claude` if you are working only in Claude Code.
- Use `wave-planner-acpx` if you want the Wave method but need workers from multiple CLIs or providers.
- Use `acpx` directly only when you need the raw CLI/session/orchestration reference rather than the full Wave skill.

</details>

<details>
<summary>Repo layout</summary>

```text
skills/
  wave-planner/
    SKILL.md
    templates/
  wave-planner-claude/
    SKILL.md
    templates/
  wave-planner-acpx/
    SKILL.md
    templates/
  acpx/
    SKILL.md
    templates/
examples/
  sample-wave-plan.md
assets/
  wave-driven-dev-banner.png
```

</details>

## Versioning

- Current version is tracked in `VERSION`
- Release history is tracked in `CHANGELOG.md`
- Tags use `vX.Y.Z`

## License

MIT. See [LICENSE](./LICENSE).
