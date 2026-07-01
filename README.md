# renovate-config

Shared [Renovate](https://docs.renovatebot.com/) configuration preset for all `minitap-ai` repositories.

## Usage

Add a `renovate.json` at the root of your repo that extends this preset:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>minitap-ai/renovate-config"]
}
```

Renovate resolves `github>minitap-ai/renovate-config` to the `default.json` preset in this repo.

## What it does

- **`prConcurrentLimit: 5`** — caps open Renovate PRs per repo (default is 10) to avoid backlog.
- **`minimumReleaseAge: "14 days"`** — waits 14 days after a release before proposing it (skips buggy day-0 releases). Bypassed for security updates.
- **Schedule** — opens PRs only Tue/Wed/Thu mornings, keeping Mondays and Fridays quiet.
- **Automerge (low-risk):** patch/pin/digest updates, minor+patch devDependencies, and GitHub Actions updates are automerged once required checks pass.
- **Major updates** are never automerged and get a `breaking-change-review` label.
- **Security / vulnerability alerts** are prioritized, unscheduled (open immediately), and labeled `security`.

## Per-repo overrides

Repos can add their own `packageRules` after the `extends` to override anything for their specific stack. Keep overrides minimal — prefer improving the shared preset so every repo benefits.
