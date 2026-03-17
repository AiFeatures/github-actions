# Deploy Supabase Migrations

Run Supabase database migrations

## Usage

```yaml
- uses: Ai-road-4-You/github-actions/deploy-supabase@v1
  with:
    supabase-access-token: # required
    project-id: # required
    db-password: # required
    working-directory: "."
    run-seed: "false"
    generate-types: "false"
```

## Inputs

| Input | Description | Required | Default |
|---|---|---|---|
| `supabase-access-token` | Supabase access token | Yes | `` |
| `project-id` | Supabase project ID | Yes | `` |
| `db-password` | Database password | Yes | `` |
| `working-directory` | Working directory (must contain supabase/ directory) | No | `.` |
| `run-seed` | Run seed file after migration | No | `false` |
| `generate-types` | Generate TypeScript types after migration | No | `false` |

## Outputs

| Output | Description |
|---|---|
| `migration-status` | Migration status (success or failure) |
| `types-path` | Path to generated types file |

## Versioning

This action follows [semantic versioning](../VERSIONING.md).
Use `@v1` for the latest backward-compatible version, or pin to an exact tag like `@v1.1.0`.

## License

See [LICENSE](../LICENSE).
