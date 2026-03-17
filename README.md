# iAiFy Enterprise — Reusable GitHub Actions

Shared composite actions for all repositories in the **iAiFy GitHub Enterprise**.

## Quick Start

Reference any action using the full path with a version tag:

```yaml
- uses: Ai-road-4-You/github-actions/setup-node@v1
  with:
    node-version: "22"
```

> Pin to a **major version tag** (`@v1`) for automatic minor/patch updates, or to an **exact version** (`@v1.0.0`) for maximum stability. Do not use `@main` in production workflows. See [VERSIONING.md](VERSIONING.md) for details.

---

## Actions

### setup-node

Setup Node.js with pnpm/npm/yarn caching and automatic dependency installation.

```yaml
- uses: Ai-road-4-You/github-actions/setup-node@v1
  with:
    node-version: "22"
    package-manager: "pnpm"
    pnpm-version: "9"
    install: "true"
    working-directory: "."
```

| Output | Description |
|--------|-------------|
| `node-version` | Installed Node.js version |
| `cache-hit` | Whether the cache was hit |

---

### setup-python

Setup Python with pip/poetry/uv caching and automatic dependency installation.

```yaml
- uses: Ai-road-4-You/github-actions/setup-python@v1
  with:
    python-version: "3.12"
    package-manager: "pip"
    requirements-file: "requirements.txt"
    install: "true"
```

| Output | Description |
|--------|-------------|
| `python-version` | Installed Python version |

---

### setup-terraform

Setup Terraform with plugin caching, init, fmt check, and validate.

```yaml
- uses: Ai-road-4-You/github-actions/setup-terraform@v1
  with:
    terraform-version: "latest"
    working-directory: "infra/"
    init: "true"
    validate: "true"
    fmt-check: "true"
```

| Output | Description |
|--------|-------------|
| `terraform-version` | Installed version |
| `init-status` | Init exit code |
| `fmt-status` | Format check exit code |

---

### docker-build-push

Build and push container images to GHCR with multi-arch support.

```yaml
- uses: Ai-road-4-You/github-actions/docker-build-push@v1
  with:
    password: ${{ secrets.GITHUB_TOKEN }}
    platforms: "linux/amd64,linux/arm64"
    push: "true"
```

| Output | Description |
|--------|-------------|
| `image` | Full image reference with tags |
| `digest` | Image digest |
| `metadata` | Build metadata JSON |

---

### security-scan

Run Trivy vulnerability scanning, npm audit, and secret scanning.

```yaml
- uses: Ai-road-4-You/github-actions/security-scan@v1
  with:
    scan-type: "trivy,secrets"
    trivy-severity: "CRITICAL,HIGH"
    trivy-exit-code: "1"
```

| Output | Description |
|--------|-------------|
| `trivy-results` | Path to Trivy results file |
| `vulnerabilities-found` | Whether vulnerabilities were found |

---

### auto-release

Semantic versioning with automatic changelog generation.

```yaml
- uses: Ai-road-4-You/github-actions/auto-release@v1
  with:
    github-token: ${{ secrets.GITHUB_TOKEN }}
    branches: "main"
    tag-format: "v${version}"
```

| Output | Description |
|--------|-------------|
| `released` | Whether a release was created |
| `version` | Released version number |
| `tag` | Git tag |

---

### cost-check

Infracost cost estimation for Terraform changes.

```yaml
- uses: Ai-road-4-You/github-actions/cost-check@v1
  with:
    api-key: ${{ secrets.INFRACOST_API_KEY }}
    working-directory: "infra/"
```

---

### verify-attestation

Verify artifact provenance attestations.

```yaml
- uses: Ai-road-4-You/github-actions/verify-attestation@v1
  with:
    artifact: "my-artifact"
    owner: "Ai-road-4-You"
```

---

### label-pr

Auto-label pull requests based on changed files.

```yaml
- uses: Ai-road-4-You/github-actions/label-pr@v1
  with:
    github-token: ${{ secrets.GITHUB_TOKEN }}
```

---

### notify-slack

Send Slack notifications for build status.

```yaml
- uses: Ai-road-4-You/github-actions/notify-slack@v1
  with:
    webhook-url: ${{ secrets.SLACK_WEBHOOK_URL }}
    status: ${{ job.status }}
```

---

### deploy-vercel

Deploy to Vercel with preview and production support.

```yaml
- uses: Ai-road-4-You/github-actions/deploy-vercel@v1
  with:
    vercel-token: ${{ secrets.VERCEL_TOKEN }}
    vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
    vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}
    production: "true"
```

| Output | Description |
|--------|-------------|
| `url` | Deployment URL |

---

### deploy-fly

Deploy applications to Fly.io.

```yaml
- uses: Ai-road-4-You/github-actions/deploy-fly@v1
  with:
    fly-api-token: ${{ secrets.FLY_API_TOKEN }}
    app-name: "my-app"
    strategy: "rolling"
```

| Output | Description |
|--------|-------------|
| `url` | Deployed application URL |
| `app-name` | Fly.io app name |

---

### deploy-railway

Deploy applications to Railway.

```yaml
- uses: Ai-road-4-You/github-actions/deploy-railway@v1
  with:
    railway-token: ${{ secrets.RAILWAY_TOKEN }}
    service: "web"
    environment: "production"
```

| Output | Description |
|--------|-------------|
| `url` | Deployed service URL |
| `deployment-id` | Railway deployment ID |

---

### deploy-supabase

Run Supabase database migrations.

```yaml
- uses: Ai-road-4-You/github-actions/deploy-supabase@v1
  with:
    supabase-access-token: ${{ secrets.SUPABASE_ACCESS_TOKEN }}
    project-id: ${{ secrets.SUPABASE_PROJECT_ID }}
    db-password: ${{ secrets.SUPABASE_DB_PASSWORD }}
    generate-types: "true"
```

| Output | Description |
|--------|-------------|
| `migration-status` | success or failure |
| `types-path` | Path to generated TypeScript types |

---

### deploy-firebase

Deploy to Firebase Hosting, Functions, Firestore, or Storage.

```yaml
- uses: Ai-road-4-You/github-actions/deploy-firebase@v1
  with:
    firebase-token: ${{ secrets.FIREBASE_TOKEN }}
    project-id: "my-project"
    targets: "hosting,functions"
```

| Output | Description |
|--------|-------------|
| `url` | Deployed URL |
| `channel-url` | Preview channel URL |

---

## Versioning

See [VERSIONING.md](VERSIONING.md) for the full versioning strategy. See [CHANGELOG.md](CHANGELOG.md) for release history.

## Contributing

1. Create a feature branch
2. Follow [Conventional Commits](https://www.conventionalcommits.org/)
3. Open a PR (CODEOWNERS will auto-request review)
4. After merge, a new release is cut automatically
