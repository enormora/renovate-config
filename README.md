# renovate-config

Shared Renovate presets for Enormora repositories.

## Usage

Use the base preset and one automerge preset.

Merge queue repositories:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": [
    "github>enormora/renovate-config#1.0.0",
    "github>enormora/renovate-config:github-automerge#1.0.0"
  ]
}
```

Repositories without a merge queue:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": [
    "github>enormora/renovate-config#1.0.0",
    "github>enormora/renovate-config:renovate-automerge#1.0.0"
  ]
}
```

Node.js 22 support:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": [
    "github>enormora/renovate-config#1.0.0",
    "github>enormora/renovate-config:renovate-automerge#1.0.0",
    "github>enormora/renovate-config:node22#1.0.0"
  ]
}
```

Local project settings stay local:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": [
    "github>enormora/renovate-config#1.0.0",
    "github>enormora/renovate-config:github-automerge#1.0.0"
  ],
  "ignorePaths": [
    "**/node_modules/**",
    "**/integration-tests/**"
  ]
}
```

Pinned preset versions use Git tags. Renovate updates pinned preset versions when a newer tag exists.

## Presets

- `default.json`: base policy, labels, release age, PR automerge, lock file maintenance, GitHub Action digest pinning, linting grouping, `@packtory/*` grouping.
- `github-automerge.json`: GitHub performs automerges. Use for merge queues.
- `renovate-automerge.json`: Renovate performs automerges during its own runs.
- `node22.json`: pins the npm tool constraint below npm 11 for Node.js 22 projects.
