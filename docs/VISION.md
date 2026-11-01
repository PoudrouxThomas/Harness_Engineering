# Vision

This repository is a demonstration of harness engineering. The product is a means; the harness is the point.

## The product

A public **toolbox** web app: a growing collection of small, self-contained **tools** (a JSON formatter, a regex tester, a dice roller…), each one requested by a visitor through a feedback form.

Every tool page shows:

- the tool itself;
- its **timeline**: every stage from raw idea to merge, each marked as done by a human or by a bot;
- its **build metrics**: tokens, model, iterations, defects by catch layer, time to ship, post-release bugs, and what was hard.

A global metrics page shows medians across all tools and overall harness efficiency.

### What is on-topic

An idea is on-topic when it fits as a **self-contained tool** that runs entirely in the visitor's browser:

- **data stays on the visitor's device**: `localStorage` and `sessionStorage` only; no cookies, nothing in the app database;
- **no external communication**: no calls to any external API;
- no payments, no user accounts.

This protects visitor data, and makes it pointless to submit a raw idea designed to collect it (ADR-0013).

Off-topic or impossible ideas are closed as `wontfix` with a reason.

## The pipeline

```
form → raw idea (app database)
     → triage routine          (bot)    → issue: ready-for-human | needs-info | wontfix
     → grilling                (human)  → ready-for-agent
     → build routine           (bot)    → worktree issue/<n>-<slug> → PR
     → review                  (human; agents later, never on harness paths)
     → merge                            → issue closed, tool live
```

The owner's place in the loop is **deciding what gets built**: the only path to `ready-for-agent` is the owner's grilling.

## Non-negotiables

- **Raw ideas never reach GitHub.** Visitor text is hostile input; only the triage routine's rewrite becomes an issue.
- **Only the owner changes the harness.** Hooks block agents locally; GitHub enforces it server-side through a separate bot identity.
- **One definition of done.** `npm run verify` is the same command for agents, hooks and CI.
- **Deterministic by construction.** Pinned toolchains, frozen clocks, seeded randomness, throwaway databases, containerised browsers.
- **Clean metrics.** Build tokens are measured separately from every other stage.

## Milestones

Each milestone starts only when the previous one's metrics justify it.

1. **Harness**: security hooks → clean-code hooks → coding loop (verify, worktrees, skills, metrics) → confirmation (CI, e2e).
2. **First tools**: built locally, owner and agents together, to collect baseline metrics.
3. **Go live**: hosting chosen, app deployed.
4. **Intake**: feedback form and triage routine.
5. **Build routine**: `ready-for-agent` issues become PRs autonomously.
6. **Agent review**: agents review and merge non-harness PRs once metrics earn it.
