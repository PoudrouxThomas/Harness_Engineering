# Harness changes are blocked by hooks and enforced through a separate bot identity

Only the owner may change the harness (`.claude/`, `.github/`, `harness/`, `AGENTS.md`, CODEOWNERS, triage prompts). Hooks alone are insufficient: they run inside the agent's own environment, can be bypassed through Bash, and are not loaded by every session type. Routines would otherwise push as the owner, so GitHub could not tell them apart. Agents therefore act as a dedicated bot account, and enforcement lives server-side.

## Consequences

- Ruleset 1 (no bypass, owner included): PR-only to `main`, required `verify` check, no force-push.
- Ruleset 2: one approval required; owner may bypass via PR only (GitHub forbids self-approval).
- A CI guard fails any bot-authored PR touching harness paths; CODEOWNERS names the owner on them.
- The human/bot source of each timeline step is derived from the GitHub actor.

## Considered Options

- **Hooks only**: rejected, see above.
- **Signed commits from an owner-only key**: works against cloud routines but not against local agents, which share the owner's key.
