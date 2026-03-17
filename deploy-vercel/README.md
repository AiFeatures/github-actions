# Deploy to Vercel

Deploy to Vercel with preview and production support

## Usage

```yaml
- uses: Ai-road-4-You/github-actions/deploy-vercel@v1
  with:
    vercel-token: # required
    vercel-org-id: # required
    vercel-project-id: # required
    production: "false"
    working-directory: "."
    build-command: # optional
    environment-variables: # optional
```

## Inputs

| Input | Description | Required | Default |
|---|---|---|---|
| `vercel-token` | Vercel API token | Yes | `` |
| `vercel-org-id` | Vercel organization ID | Yes | `` |
| `vercel-project-id` | Vercel project ID | Yes | `` |
| `production` | Deploy to production (false = preview) | No | `false` |
| `working-directory` | Working directory | No | `.` |
| `build-command` | Override the build command | No | `` |
| `environment-variables` | Environment variables to set (newline-separated KEY=VALUE) | No | `` |

## Outputs

| Output | Description |
|---|---|
| `url` | Deployment URL |
| `preview-url` | Preview URL (alias for url) |

## Versioning

This action follows [semantic versioning](../VERSIONING.md).
Use `@v1` for the latest backward-compatible version, or pin to an exact tag like `@v1.1.0`.

## License

See [LICENSE](../LICENSE).
