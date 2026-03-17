# Setup Terraform

Setup Terraform with caching and optional init

## Usage

```yaml
- uses: Ai-road-4-You/github-actions/setup-terraform@v1
  with:
    terraform-version: "latest"
    working-directory: "."
    init: "true"
    backend-config: # optional
    cli-config-credentials-token: # optional
    fmt-check: "false"
    validate: "false"
```

## Inputs

| Input | Description | Required | Default |
|---|---|---|---|
| `terraform-version` | Terraform version to install | No | `latest` |
| `working-directory` | Working directory containing Terraform files | No | `.` |
| `init` | Run terraform init after setup | No | `true` |
| `backend-config` | Backend configuration arguments (newline-separated key=value) | No | `` |
| `cli-config-credentials-token` | Terraform Cloud / HCP token | No | `` |
| `fmt-check` | Run terraform fmt -check | No | `false` |
| `validate` | Run terraform validate after init | No | `false` |

## Outputs

| Output | Description |
|---|---|
| `terraform-version` | Installed Terraform version |
| `init-status` | Terraform init exit code |
| `fmt-status` | Terraform fmt check exit code |
| `validate-status` | Terraform validate exit code |

## Versioning

This action follows [semantic versioning](../VERSIONING.md).
Use `@v1` for the latest backward-compatible version, or pin to an exact tag like `@v1.1.0`.

## License

See [LICENSE](../LICENSE).
