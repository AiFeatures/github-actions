# verify-attestation

Verify artifact attestation provenance

## Usage

```yaml
- uses: Ai-road-4-You/github-actions/verify-attestation@v1
  with:
    artifact: # required
    owner: # optional
```

## Inputs

| Input | Description | Required | Default |
|---|---|---|---|
| `artifact` | Path to artifact or container image to verify | Yes | `` |
| `owner` | GitHub owner (org) for attestation verification | No | `` |

## Versioning

This action follows [semantic versioning](../VERSIONING.md).
Use `@v1` for the latest backward-compatible version, or pin to an exact tag like `@v1.1.0`.

## License

See [LICENSE](../LICENSE).
