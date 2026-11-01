# Harness Engineering

A public toolbox web app whose real product is the harness that builds it: visitors request tools, agents build them, and every tool shows how it was built.

## Product

**Tool**:
A small, self-contained feature of the toolbox that a visitor can use on its own page.
_Avoid_: App, module, widget, feature

**Tool page**:
The public page of a tool, showing the tool itself, its timeline and its build metrics.

**Metrics page**:
The public page comparing all tools and showing overall harness efficiency.
_Avoid_: Dashboard, stats

## Pipeline

**Raw idea**:
A visitor's unmodified form submission, held only in the app database.
_Avoid_: Request, ticket, feedback

**Idea**:
A raw idea after triage has rewritten it into a GitHub issue.
_Avoid_: Raw idea (once triaged), suggestion

**Triage**:
The automated stage that rewrites a raw idea and judges whether it is on-topic and feasible.

**On-topic**:
Fits as a self-contained tool whose data stays on the visitor's device and that communicates with no external API.
_Avoid_: In scope, relevant

**Grilling**:
The owner's interview of an idea that turns it into a fully specified issue ready for an agent.
_Avoid_: Refinement, review

**Build**:
The stage in which an agent implements a `ready-for-agent` issue up to an open PR.
_Avoid_: Implementation run, job

**Review**:
The stage in which a PR is checked before merge, by the owner or later by an agent.

**Stage**:
One of triage, grilling, build, review or retro; the unit by which timeline steps and tokens are attributed.
_Avoid_: Phase, step (for this meaning)

**Timeline**:
The ordered, timestamped record of every stage a tool went through, each marked with its source.

**Source**:
Whether a timeline step was performed by a human or by the bot.
_Avoid_: Actor, author

## Harness

**Harness**:
Everything that shapes and checks agent work: hooks, skills, verification scripts, CI, routines, agent instructions.
_Avoid_: Framework, tooling, infra

**Harness path**:
A file location belonging to the harness, which only the owner may change.
_Avoid_: Protected file, config

**Owner**:
The single human who decides what is built and alone changes the harness.
_Avoid_: Admin, maintainer, user

**Bot**:
The dedicated GitHub identity under which agents push, open PRs and label issues.
_Avoid_: Agent account, Claude

**Visitor**:
Anyone using the public app, including those who submit raw ideas.
_Avoid_: User, requester, customer

**Routine**:
A cloud agent run triggered on a schedule or by a GitHub event.
_Avoid_: Scheduled task, cron job, workflow

**Milestone**:
One step of the roadmap toward autonomy, unlocked when the previous one's metrics justify it.
_Avoid_: Phase

## Metrics

**Iteration**:
One fix attempt by an agent that ends in a verification run, counted until verification passes.
_Avoid_: Retry, loop

**Catch layer**:
The harness layer that caught a defect: hook, verification, CI, review, or a visitor after release.
_Avoid_: Gate, check

**Escaped defect**:
A defect found by a visitor after the tool was released.
_Avoid_: Production bug

**Retro**:
The agent's short self-report on what was hard in a build, kept out of build token counts.
_Avoid_: Postmortem, summary
