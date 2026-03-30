# acpx Model Routing (Edit Before Real Use)

If this file still contains the placeholder warning below, stop and ask the user to update it first.

PLACEHOLDER WARNING:
- Model routing is not customized yet.
- Edit the model order below to match installed/available providers.
- Remove this warning after customization.

## Routing Order

hard tasks:
- codex
- claude
- gemini

middle tasks:
- codex
- claude
- gemini

easy tasks:
- gemini
- claude
- codex

## Selection Rules

- Classify each worker task as `hard`, `middle`, or `easy`.
- Try models in listed order for that class.
- If model is unavailable or fails, fallback to next model in same class.
- If all models fail, stop and ask user how to proceed.
