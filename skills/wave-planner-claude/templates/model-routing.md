# Model Routing for Claude Code

Claude Code supports three model tiers via the Agent tool's `model` parameter.

## Available Models

| Model    | ID        | Best for                                      |
|----------|-----------|-----------------------------------------------|
| Haiku    | `haiku`   | Well-scoped tasks, simple edits, test runs    |
| Sonnet   | `sonnet`  | Medium complexity, multi-file logic changes   |
| Opus     | `opus`    | Complex architecture, nuanced reasoning       |

## Routing Order

hard tasks:
- opus
- sonnet

middle tasks:
- sonnet
- opus

easy tasks:
- sonnet
- opus

## Selection Rules

- Classify each worker task as `hard`, `middle`, or `easy`.
- Default to `sonnet` for all workers.
- If `sonnet` produces poor results on a complex task, escalate to `opus` with user approval.
- Only use `opus` for workers with user approval.
- Prefer a stronger plan over a stronger model — clear instructions make `sonnet` sufficient for most scoped tasks.

## Cost Considerations

- `sonnet` is the default for all worker execution — good balance of capability and cost.
- `opus` should be reserved for tasks that genuinely require deep reasoning or complex architectural decisions.
- Always ask the user before escalating to `opus`.
