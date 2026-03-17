# Docker Build & Push

Build and push Docker images to GHCR with multi-arch support

## Usage

```yaml
- uses: Ai-road-4-You/github-actions/docker-build-push@v1
  with:
    image-name: "${{ github.repository }}"
    registry: "ghcr.io"
    username: "${{ github.actor }}"
    password: # required
    context: "."
    file: "./Dockerfile"
    platforms: "linux/amd64"
    push: "true"
    tags: # optional
    build-args: # optional
    cache-from: "type=gha"
    cache-to: "type=gha,mode=max"
```

## Inputs

| Input | Description | Required | Default |
|---|---|---|---|
| `image-name` | Image name (without registry prefix) | No | `${{ github.repository }}` |
| `registry` | Container registry | No | `ghcr.io` |
| `username` | Registry username | No | `${{ github.actor }}` |
| `password` | Registry password / token | Yes | `` |
| `context` | Docker build context | No | `.` |
| `file` | Path to Dockerfile | No | `./Dockerfile` |
| `platforms` | Target platforms for multi-arch build | No | `linux/amd64` |
| `push` | Push the image after building | No | `true` |
| `tags` | Additional tags (newline-separated, added to auto-generated tags) | No | `` |
| `build-args` | Docker build arguments (newline-separated KEY=VALUE) | No | `` |
| `cache-from` | Cache source | No | `type=gha` |
| `cache-to` | Cache destination | No | `type=gha,mode=max` |

## Outputs

| Output | Description |
|---|---|
| `image` | Full image reference (registry/name:tag) |
| `digest` | Image digest |
| `metadata` | Build metadata JSON |

## Versioning

This action follows [semantic versioning](../VERSIONING.md).
Use `@v1` for the latest backward-compatible version, or pin to an exact tag like `@v1.1.0`.

## License

See [LICENSE](../LICENSE).
