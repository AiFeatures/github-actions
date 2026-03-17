# Cloud Cost Check

Run Infracost cloud cost estimation on Terraform changes

## Usage

```yaml
- uses: Ai-road-4-You/github-actions/cost-check@v1
  with:
    api-key: # required
    working-directory: "."
    currency: "USD"
    show-skipped: "false"
    post-comment: "true"
    github-token: # optional
    threshold-percentage: "10"
```

## Inputs

| Input | Description | Required | Default |
|---|---|---|---|
| `api-key` | Infracost API key | Yes | `` |
| `working-directory` | Working directory containing Terraform files | No | `.` |
| `currency` | Currency for cost output | No | `USD` |
| `show-skipped` | Show skipped resources in output | No | `false` |
| `post-comment` | Post cost diff as PR comment | No | `true` |
| `github-token` | GitHub token for posting PR comments | No | `` |
| `threshold-percentage` | Warn if cost increase exceeds this percentage | No | `10` |

## Outputs

| Output | Description |
|---|---|
| `monthly-cost` | Estimated total monthly cost |
| `diff-monthly-cost` | Monthly cost difference from baseline |
| `cost-increased` | Whether costs increased beyond threshold |

## Versioning

This action follows [semantic versioning](../VERSIONING.md).
Use `@v1` for the latest backward-compatible version, or pin to an exact tag like `@v1.1.0`.

## License

See [LICENSE](../LICENSE).
