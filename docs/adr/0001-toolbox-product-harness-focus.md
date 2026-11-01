# The product is a toolbox of isolated tools, built in public

The repo exists to demonstrate harness engineering, so the product had to offer an endless, low-conflict backlog. We chose a toolbox of small self-contained tools over a custom agent harness (no objective oracle, LLM output is non-deterministic to test) and over a single-domain app (features couple, worktrees conflict). Each tool's page publishes how it was built, which makes the harness itself the visible product.

## Considered Options

- **Custom coding harness / LLM gateway**: most AI learning, but verification becomes its own project and "what next" drifts into cloning existing tools.
- **Redis or jq clone**: excellent oracle, but not something visitors can request features for.
