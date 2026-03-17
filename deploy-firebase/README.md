# Deploy to Firebase

Deploy to Firebase Hosting, Functions, or Firestore rules

## Usage

```yaml
- uses: Ai-road-4-You/github-actions/deploy-firebase@v1
  with:
    firebase-token: # optional
    google-application-credentials: # optional
    project-id: # required
    targets: "hosting"
    working-directory: "."
    channel: # optional
    expires: "7d"
```

## Inputs

| Input | Description | Required | Default |
|---|---|---|---|
| `firebase-token` | Firebase CI token (or use google-application-credentials) | No | `` |
| `google-application-credentials` | Google service account JSON key (base64 encoded) | No | `` |
| `project-id` | Firebase project ID | Yes | `` |
| `targets` | Firebase deploy targets (comma-separated: hosting, functions, firestore, storage) | No | `hosting` |
| `working-directory` | Working directory | No | `.` |
| `channel` | Firebase Hosting preview channel name (leave empty for live deploy) | No | `` |
| `expires` | Preview channel expiry (e.g., 7d, 30d) | No | `7d` |

## Outputs

| Output | Description |
|---|---|
| `url` | Deployed URL |
| `channel-url` | Preview channel URL (if using channels) |

## Versioning

This action follows [semantic versioning](../VERSIONING.md).
Use `@v1` for the latest backward-compatible version, or pin to an exact tag like `@v1.1.0`.

## License

See [LICENSE](../LICENSE).
