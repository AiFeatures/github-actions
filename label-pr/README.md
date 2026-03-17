# Auto-Label PR

Automatically label pull requests based on changed file paths

## Usage

```yaml
- uses: Ai-road-4-You/github-actions/label-pr@v1
  with:
    github-token: # required
    config: "frontend:
  - "src/app/**"
  - "src/components/**"
  - "*.css"
  - "*.scss"
  - "*.tsx"
backend:
  - "src/api/**"
  - "src/server/**"
  - "src/lib/**"
documentation:
  - "docs/**"
  - "**/*.md"
  - "*.md"
tests:
  - "**/*.test.*"
  - "**/*.spec.*"
  - "__tests__/**"
  - "tests/**"
  - "test/**"
ci:
  - ".github/**"
  - "Dockerfile"
  - "docker-compose*"
dependencies:
  - "package.json"
  - "pnpm-lock.yaml"
  - "package-lock.json"
  - "yarn.lock"
  - "requirements*.txt"
  - "pyproject.toml"
  - "go.mod"
infrastructure:
  - "terraform/**"
  - "*.tf"
  - "infra/**"
database:
  - "**/migrations/**"
  - "supabase/**"
  - "prisma/**"
  - "drizzle/**"
"
    config-file: # optional
    sync-labels: "false"
```

## Inputs

| Input | Description | Required | Default |
|---|---|---|---|
| `github-token` | GitHub token with pull-requests:write permission | Yes | `` |
| `config` | Label configuration as YAML (label: glob patterns) | No | `frontend:
  - "src/app/**"
  - "src/components/**"
  - "*.css"
  - "*.scss"
  - "*.tsx"
backend:
  - "src/api/**"
  - "src/server/**"
  - "src/lib/**"
documentation:
  - "docs/**"
  - "**/*.md"
  - "*.md"
tests:
  - "**/*.test.*"
  - "**/*.spec.*"
  - "__tests__/**"
  - "tests/**"
  - "test/**"
ci:
  - ".github/**"
  - "Dockerfile"
  - "docker-compose*"
dependencies:
  - "package.json"
  - "pnpm-lock.yaml"
  - "package-lock.json"
  - "yarn.lock"
  - "requirements*.txt"
  - "pyproject.toml"
  - "go.mod"
infrastructure:
  - "terraform/**"
  - "*.tf"
  - "infra/**"
database:
  - "**/migrations/**"
  - "supabase/**"
  - "prisma/**"
  - "drizzle/**"
` |
| `config-file` | Path to label config file (overrides config input) | No | `` |
| `sync-labels` | Remove labels when files no longer match | No | `false` |

## Outputs

| Output | Description |
|---|---|
| `labels-added` | Comma-separated list of labels added |
| `labels-removed` | Comma-separated list of labels removed |

## Versioning

This action follows [semantic versioning](../VERSIONING.md).
Use `@v1` for the latest backward-compatible version, or pin to an exact tag like `@v1.1.0`.

## License

See [LICENSE](../LICENSE).
