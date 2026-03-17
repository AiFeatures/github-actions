# Auto Release

Create semantic releases with changelog generation

## Usage

```yaml
- uses: Ai-road-4-You/github-actions/auto-release@v1
  with:
    github-token: # required
    npm-token: # optional
    release-type: # optional
    dry-run: "false"
    working-directory: "."
    extra-plugins: # optional
    branches: "main"
    tag-format: "v${version}"
```

## Inputs

| Input | Description | Required | Default |
|---|---|---|---|
| `github-token` | GitHub token with contents:write permission | Yes | `` |
| `npm-token` | NPM token (for publishing to npm) | No | `` |
| `release-type` | Force release type (patch, minor, major) — empty = auto-detect from commits | No | `` |
| `dry-run` | Run in dry-run mode (no actual release) | No | `false` |
| `working-directory` | Working directory | No | `.` |
| `extra-plugins` | Additional semantic-release plugins (comma-separated npm package names) | No | `` |
| `branches` | Release branches (comma-separated) | No | `main` |
| `tag-format` | Tag format (use ${version} as placeholder) | No | `v${version}` |

## Outputs

| Output | Description |
|---|---|
| `released` | Whether a new release was created |
| `version` | Released version |
| `tag` | Git tag for the release |
| `changelog` | Release changelog |

## Versioning

This action follows [semantic versioning](../VERSIONING.md).
Use `@v1` for the latest backward-compatible version, or pin to an exact tag like `@v1.1.0`.

## License

See [LICENSE](../LICENSE).
