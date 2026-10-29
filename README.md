# triagedaemon.github.io

The website for Triage Daemon, escalation triage: **https://triagedaemon.github.io**

This repo holds no content of its own. The pages are written in the private repo
`triagedaemon/triaged` under `docs/` (with `mkdocs.yml`),
and the [Deploy site](.github/workflows/deploy.yml) workflow builds them with MkDocs Material and
publishes them with GitHub Pages.

- **Edit the docs:** open a pull request against `docs/` in `triagedaemon/triaged` (members only).
- **When changes go live:** within a minute when `triaged` has a `SITE_DISPATCH_TOKEN` secret (see below); otherwise at the next hourly run. To publish now: *Actions → Deploy site → Run workflow*.

### Reading the private source (required)

`triaged` is private, so the deploy needs a token to check it out:

1. Create a fine-grained personal access token: resource owner `triagedaemon`, repository access *only* `triagedaemon/triaged`, permission **Contents: Read-only**. Nothing else. Set an expiry and a reminder to renew it.
2. In this repo (`triagedaemon.github.io`), go to *Settings → Secrets and variables → Actions* and add it as `TRIAGED_READ_TOKEN`.

Without the secret, the build fails at "Check out the docs source" and the site keeps the last version that was published.

### Instant deploys (optional)

1. Create a fine-grained personal access token: resource owner `triagedaemon`, repository access *only* `triagedaemon.github.io`, permission **Contents: Read and write** (needed to send a `repository_dispatch`). Nothing else.
2. In `triagedaemon/triaged`, go to *Settings → Secrets and variables → Actions* and add it as `SITE_DISPATCH_TOKEN`.

The Docs workflow in `triaged` then pings this repo after every docs change on `main`. Without the secret that step is skipped and the hourly schedule still publishes.

Copyright 2026 The Triage Daemon Authors. All rights reserved: viewing the site is permitted; copying, hosting or reusing it needs written permission. See the [licence](https://triagedaemon.github.io/licence/). To ask for permission, open an issue in this repo.
