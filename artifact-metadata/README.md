# Artifact Metadata

Generate standardized artifact metadata JSON with all 20 required fields per iAiFy TOM

## Usage

```yaml
- uses: Ai-road-4-You/github-actions/artifact-metadata@v1
  with:
    artifact-type: # required
    semantic-version: # optional
    target-environment: # optional
    sbom-reference: # optional
    signature-status: "unsigned"
    provenance-reference: # optional
    retention-class: "standard"
    owner-team: # optional
    project: # optional
    output-path: "artifact-metadata.json"
    upload: "true"
```

## Inputs

| Input | Description | Required | Default |
|---|---|---|---|
| `artifact-type` | Artifact type (container, npm-package, release-bundle, test-report, sbom, security-scan) | Yes | `` |
| `semantic-version` | Semantic version | No | `` |
| `target-environment` | Target deployment environment | No | `` |
| `sbom-reference` | SBOM file path or URL | No | `` |
| `signature-status` | Signature status (signed, unsigned, pending) | No | `unsigned` |
| `provenance-reference` | Provenance attestation reference | No | `` |
| `retention-class` | Retention class (ephemeral, standard, extended, permanent) | No | `standard` |
| `owner-team` | Owner team | No | `` |
| `project` | Project name | No | `` |
| `output-path` | Output path for metadata JSON | No | `artifact-metadata.json` |
| `upload` | Upload metadata as workflow artifact | No | `true` |

## Outputs

| Output | Description |
|---|---|
| `metadata-path` | Path to generated metadata JSON |

## Versioning

This action follows [semantic versioning](../VERSIONING.md).
Use `@v1` for the latest backward-compatible version, or pin to an exact tag like `@v1.1.0`.

## License

See [LICENSE](../LICENSE).
