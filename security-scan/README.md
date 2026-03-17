# Security Scan

Run Trivy vulnerability scan, npm audit, and secret scanning

## Usage

```yaml
- uses: Ai-road-4-You/github-actions/security-scan@v1
  with:
    scan-type: "trivy,secrets"
    trivy-scan-type: "fs"
    trivy-severity: "CRITICAL,HIGH"
    trivy-exit-code: "1"
    image-ref: # optional
    working-directory: "."
    upload-sarif: "true"
```

## Inputs

| Input | Description | Required | Default |
|---|---|---|---|
| `scan-type` | Scan types to run (comma-separated: trivy,npm-audit,secrets) | No | `trivy,secrets` |
| `trivy-scan-type` | Trivy scan type (fs, image, config) | No | `fs` |
| `trivy-severity` | Trivy severity levels to report | No | `CRITICAL,HIGH` |
| `trivy-exit-code` | Trivy exit code on findings (1 = fail the job) | No | `1` |
| `image-ref` | Container image to scan (for trivy image scan) | No | `` |
| `working-directory` | Working directory | No | `.` |
| `upload-sarif` | Upload SARIF results to GitHub Security tab | No | `true` |

## Outputs

| Output | Description |
|---|---|
| `trivy-results` | Path to Trivy results file |
| `vulnerabilities-found` | Whether vulnerabilities were found |

## Versioning

This action follows [semantic versioning](../VERSIONING.md).
Use `@v1` for the latest backward-compatible version, or pin to an exact tag like `@v1.1.0`.

## License

See [LICENSE](../LICENSE).
