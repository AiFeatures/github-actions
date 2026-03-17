# Deploy to Railway

Deploy an application to Railway

## Usage

```yaml
- uses: Ai-road-4-You/github-actions/deploy-railway@v1
  with:
    railway-token: # required
    service: # optional
    environment: "production"
    working-directory: "."
    wait: "true"
```

## Inputs

| Input | Description | Required | Default |
|---|---|---|---|
| `railway-token` | Railway API token | Yes | `` |
| `service` | Railway service name (for multi-service projects) | No | `` |
| `environment` | Railway environment (production, staging) | No | `production` |
| `working-directory` | Working directory | No | `.` |
| `wait` | Wait for deployment to complete | No | `true` |

## Outputs

| Output | Description |
|---|---|
| `url` | Deployed service URL |
| `deployment-id` | Railway deployment ID |

## Versioning

This action follows [semantic versioning](../VERSIONING.md).
Use `@v1` for the latest backward-compatible version, or pin to an exact tag like `@v1.1.0`.

## License

See [LICENSE](../LICENSE).
