# Setup Node.js

Setup Node.js with pnpm/npm caching and dependency installation

## Usage

```yaml
- uses: Ai-road-4-You/github-actions/setup-node@v1
  with:
    node-version: "22"
    package-manager: "pnpm"
    pnpm-version: "9"
    install: "true"
    working-directory: "."
    install-args: # optional
```

## Inputs

| Input | Description | Required | Default |
|---|---|---|---|
| `node-version` | Node.js version to install | No | `22` |
| `package-manager` | Package manager to use (npm, pnpm, yarn) | No | `pnpm` |
| `pnpm-version` | pnpm version (only used when package-manager is pnpm) | No | `9` |
| `install` | Run dependency installation after setup | No | `true` |
| `working-directory` | Working directory for install command | No | `.` |
| `install-args` | Additional arguments for the install command | No | `` |

## Outputs

| Output | Description |
|---|---|
| `node-version` | Installed Node.js version |
| `cache-hit` | Whether the cache was hit |

## Versioning

This action follows [semantic versioning](../VERSIONING.md).
Use `@v1` for the latest backward-compatible version, or pin to an exact tag like `@v1.1.0`.

## License

See [LICENSE](../LICENSE).
