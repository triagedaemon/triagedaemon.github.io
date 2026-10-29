# triagedaemon.github.io

The website for [Triage Daemon](https://github.com/triagedaemon/triaged), escalation triage: **https://triagedaemon.github.io**

This repo holds no content of its own. The pages are written in
[`triagedaemon/triaged`](https://github.com/triagedaemon/triaged) under `docs/` (with `mkdocs.yml`),
and the [Deploy site](.github/workflows/deploy.yml) workflow builds them with MkDocs Material and
publishes them with GitHub Pages.

- **Edit the docs:** open a pull request against `docs/` in [triagedaemon/triaged](https://github.com/triagedaemon/triaged).
- **When changes go live:** within a minute when `triaged` has a `SITE_DISPATCH_TOKEN` secret (see below); otherwise at the next hourly run. To publish now: *Actions → Deploy site → Run workflow*.

### Instant deploys (optional)

1. Create a fine-grained personal access token: resource owner `triagedaemon`, repository access *only* `triagedaemon.github.io`, permission **Contents: Read and write** (needed to send a `repository_dispatch`). Nothing else.
2. In `triagedaemon/triaged`, go to *Settings → Secrets and variables → Actions* and add it as `SITE_DISPATCH_TOKEN`.

The Docs workflow in `triaged` then pings this repo after every docs change on `main`. Without the secret that step is skipped and the hourly schedule still publishes.

Copyright 2026 The Triage Daemon Authors. All rights reserved: viewing the site is permitted; copying, hosting or reusing it needs written permission. See the [licence](https://github.com/triagedaemon/triaged/blob/main/LICENSE).
