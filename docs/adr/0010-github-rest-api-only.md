# Harness scripts talk to GitHub through the REST API only

The cloud session GitHub proxy rejects GraphQL, so `gh issue` and `gh pr` subcommands fail in routines while working locally. Harness scripts go through a shared REST helper (`gh api`), and agents are told to do the same, so nothing breaks the first time it runs in the cloud. This is about portability, not restricting agents.
