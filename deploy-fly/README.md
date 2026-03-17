# Deploy to Fly.io

Deploy an application to Fly.io

## Usage

```yaml
- uses: Ai-road-4-You/github-actions/deploy-fly@v1
  with:
    fly-api-token: # required
    app-name: # optional
    config: "fly.toml"
    region: # optional
    working-directory: "."
    build-args: # optional
    strategy: # optional
    wait-timeout: "300"
```

## Inputs

| Input | Description | Required | Default |
|---|---|---|---|
| `fly-api-token` | Fly.io API token | Yes | `` |
| `app-name` | Fly.io app name (defaults to fly.toml config) | No | `` |
| `config` | Path to fly.toml | No | `fly.toml` |
| `region` | Fly.io region | No | `` |
| `working-directory` | Working directory | No | `.` |
| `build-args` | Docker build arguments (space-separated --build-arg KEY=VALUE) | No | `` |
| `strategy` | Deployment strategy (canary, rolling, bluegreen, immediate) | No | `` |
| `wait-timeout` | Seconds to wait for deployment to complete | No | `300` |

## Outputs

| Output | Description |
|---|---|
| `url` | Deployed application URL |
| `app-name` | Fly.io app name |

## Versioning

This action follows [semantic versioning](../VERSIONING.md).
Use `@v1` for the latest backward-compatible version, or pin to an exact tag like `@v1.1.0`.

## License

See [LICENSE](../LICENSE).
