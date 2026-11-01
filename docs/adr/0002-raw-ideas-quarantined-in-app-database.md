# Raw ideas are quarantined in the app database, never on GitHub

The repo is public, and visitor text is hostile input (spam, abuse, personal data, prompt injection). Form submissions are stored only in the app's Postgres; the triage routine reads them through an authenticated API and creates a GitHub issue containing only its own rewrite. Raw text is never published, and the triage routine has no repo checkout, shell or code access, so an injection can at worst mislabel an idea that the owner still has to grill.
