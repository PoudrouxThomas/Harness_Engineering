# The repo is public from day one and closed to outsider interaction

Building in public makes the harness story credible and gives free branch protection (GitHub Free does not enforce rulesets on private repos). The feedback form is the only intake: an Action locks every issue on creation, auto-closes and locks issues and PRs not opened by the owner or the bot, blank issues are disabled, and fork PRs run CI without secrets (`pull_request`, never `pull_request_target`). GitHub interaction limits expire after six months, so they are only a supplement.
