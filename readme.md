# renovate-config

Shared Renovate presets for Enormora repositories.

## Usage

Use the base preset and one automerge preset.

Merge queue repositories:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": [
    "github>enormora/renovate-config#1.0.2",
    "github>enormora/renovate-config:github-automerge#1.0.2"
  ]
}
```

Repositories without a merge queue:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": [
    "github>enormora/renovate-config#1.0.2",
    "github>enormora/renovate-config:renovate-automerge#1.0.2"
  ]
}
```

Node.js 22 support:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": [
    "github>enormora/renovate-config#1.0.2",
    "github>enormora/renovate-config:renovate-automerge#1.0.2",
    "github>enormora/renovate-config:node22#1.0.2"
  ]
}
```

Local project settings stay local:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": [
    "github>enormora/renovate-config#1.0.2",
    "github>enormora/renovate-config:github-automerge#1.0.2"
  ],
  "ignorePaths": [
    "**/node_modules/**",
    "**/integration-tests/**"
  ]
}
```

Pinned preset versions use Git tags. Renovate updates pinned preset versions when a newer tag exists.

Do not use commit SHAs here. Renovate can resolve them as Git refs, but it updates preset pins through the Git tags datasource.

This repo also has its own `renovate.json`. Renovate validates the presets, updates pinned preset tags in `renovate.json`, and updates tool constraints such as `constraints.npm` in `node22.json`.

## Presets

- `default.json`: base policy, labels, release age, PR automerge, lock file maintenance, GitHub Action digest pinning, linting grouping, `@packtory/*` grouping.
- `github-automerge.json`: GitHub performs automerges. Use for merge queues.
- `renovate-automerge.json`: Renovate performs automerges during its own runs.
- `node22.json`: pins the npm tool constraint below npm 11 for Node.js 22 projects.
