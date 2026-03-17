# Notify Slack

Send a Slack notification for build/deploy status

## Usage

```yaml
- uses: Ai-road-4-You/github-actions/notify-slack@v1
  with:
    webhook-url: # required
    status: # required
    title: # optional
    message: # optional
    environment: # optional
    url: # optional
    mention-on-failure: # optional
```

## Inputs

| Input | Description | Required | Default |
|---|---|---|---|
| `webhook-url` | Slack Incoming Webhook URL | Yes | `` |
| `status` | Job status (success, failure, cancelled) | Yes | `` |
| `title` | Notification title | No | `` |
| `message` | Custom message body | No | `` |
| `environment` | Deployment environment | No | `` |
| `url` | Deployment or build URL | No | `` |
| `mention-on-failure` | Slack user/group ID to mention on failure (e.g., @here, U12345) | No | `` |

## Versioning

This action follows [semantic versioning](../VERSIONING.md).
Use `@v1` for the latest backward-compatible version, or pin to an exact tag like `@v1.1.0`.

## License

See [LICENSE](../LICENSE).
