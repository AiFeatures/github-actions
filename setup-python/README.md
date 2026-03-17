# Setup Python

Setup Python with pip/poetry/uv caching and dependency installation

## Usage

```yaml
- uses: Ai-road-4-You/github-actions/setup-python@v1
  with:
    python-version: "3.12"
    package-manager: "pip"
    working-directory: "."
    requirements-file: "requirements.txt"
    install: "true"
```

## Inputs

| Input | Description | Required | Default |
|---|---|---|---|
| `python-version` | Python version to install | No | `3.12` |
| `package-manager` | Package manager to use (pip, poetry, uv) | No | `pip` |
| `working-directory` | Working directory for install command | No | `.` |
| `requirements-file` | Requirements file path (for pip) | No | `requirements.txt` |
| `install` | Run dependency installation after setup | No | `true` |

## Outputs

| Output | Description |
|---|---|
| `python-version` | Installed Python version |

## Versioning

This action follows [semantic versioning](../VERSIONING.md).
Use `@v1` for the latest backward-compatible version, or pin to an exact tag like `@v1.1.0`.

## License

See [LICENSE](../LICENSE).
