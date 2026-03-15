# iAiFy Enterprise — Reusable GitHub Actions

Shared composite actions for all repositories in the **AiFeatures** organization.

## Quick Start

Reference any action using the full path:

```yaml
- uses: AiFeatures/github-actions/setup-node@main
  with:
    node-version: "22"
```

> **Pin to a release tag** in production workflows instead of `@main`.

---

## Actions

### setup-node

Setup Node.js with pnpm/npm/yarn caching and automatic dependency installation.

```yaml
- uses: AiFeatures/github-actions/setup-node@main
  with:
    node-version: "22"           # default: 22
    package-manager: "pnpm"      # npm | pnpm | yarn (default: pnpm)
    pnpm-version: "9"            # default: 9
    install: "true"              # default: true
    working-directory: "."       # default: .
```

| Output | Description |
|--------|-------------|
| `node-version` | Installed Node.js version |
| `cache-hit` | Whether the cache was hit |

---

### setup-python

Setup Python with pip/poetry/uv caching and automatic dependency installation.

```yaml
- uses: AiFeatures/github-actions/setup-python@main
  with:
    python-version: "3.12"       # default: 3.12
    package-manager: "pip"       # pip | poetry | uv (default: pip)
    requirements-file: "requirements.txt"
    install: "true"              # default: true
```

| Output | Description |
|--------|-------------|
| `python-version` | Installed Python version |

---

### docker-build-push

Build and push container images to GHCR with multi-arch support.

```yaml
- uses: AiFeatures/github-actions/docker-build-push@main
  with:
    password: ${{ secrets.GITHUB_TOKEN }}
    platforms: "linux/amd64,linux/arm64"  # default: linux/amd64
    push: "true"
```

| Output | Description |
|--------|-------------|
| `image` | Full image reference with tags |
| `digest` | Image digest |
| `metadata` | Build metadata JSON |

Generates tags automatically from branch, PR, semver, and SHA.

---

### security-scan

Run Trivy vulnerability scanning, npm audit, and secret scanning.

```yaml
- uses: AiFeatures/github-actions/security-scan@main
  with:
    scan-type: "trivy,secrets"   # trivy | npm-audit | secrets
    trivy-severity: "CRITICAL,HIGH"
    trivy-exit-code: "1"         # fail the job on findings
```

| Output | Description |
|--------|-------------|
| `trivy-results` | Path to Trivy results file |
| `vulnerabilities-found` | Whether vulnerabilities were found |

---

### deploy-vercel

Deploy to Vercel with preview and production support.

```yaml
# Preview deployment (PRs)
- uses: AiFeatures/github-actions/deploy-vercel@main
  with:
    vercel-token: ${{ secrets.VERCEL_TOKEN }}
    vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
    vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}

# Production deployment
- uses: AiFeatures/github-actions/deploy-vercel@main
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
- uses: AiFeatures/github-actions/deploy-fly@main
  with:
    fly-api-token: ${{ secrets.FLY_API_TOKEN }}
    app-name: "my-app"           # optional, reads from fly.toml
    region: "iad"                # optional
    strategy: "rolling"          # canary | rolling | bluegreen | immediate
```

| Output | Description |
|--------|-------------|
| `url` | Deployed application URL |
| `app-name` | Fly.io app name |

---

### deploy-railway

Deploy applications to Railway.

```yaml
- uses: AiFeatures/github-actions/deploy-railway@main
  with:
    railway-token: ${{ secrets.RAILWAY_TOKEN }}
    service: "web"               # optional, for multi-service projects
    environment: "production"    # default: production
```

| Output | Description |
|--------|-------------|
| `url` | Deployed service URL |
| `deployment-id` | Railway deployment ID |

---

### deploy-supabase

Run Supabase database migrations.

```yaml
- uses: AiFeatures/github-actions/deploy-supabase@main
  with:
    supabase-access-token: ${{ secrets.SUPABASE_ACCESS_TOKEN }}
    project-id: ${{ secrets.SUPABASE_PROJECT_ID }}
    db-password: ${{ secrets.SUPABASE_DB_PASSWORD }}
    generate-types: "true"       # optional: generate TypeScript types
```

| Output | Description |
|--------|-------------|
| `migration-status` | success or failure |
| `types-path` | Path to generated TypeScript types |

---

### deploy-firebase

Deploy to Firebase Hosting, Functions, Firestore, or Storage.

```yaml
# Production deploy
- uses: AiFeatures/github-actions/deploy-firebase@main
  with:
    firebase-token: ${{ secrets.FIREBASE_TOKEN }}
    project-id: "my-project"
    targets: "hosting,functions"

# Preview channel
- uses: AiFeatures/github-actions/deploy-firebase@main
  with:
    firebase-token: ${{ secrets.FIREBASE_TOKEN }}
    project-id: "my-project"
    channel: "pr-${{ github.event.pull_request.number }}"
    expires: "7d"
```

| Output | Description |
|--------|-------------|
| `url` | Deployed URL |
| `channel-url` | Preview channel URL |

---

### auto-release

Semantic versioning with automatic changelog generation.

```yaml
- uses: AiFeatures/github-actions/auto-release@main
  with:
    github-token: ${{ secrets.GITHUB_TOKEN }}
    branches: "main"             # default: main
    tag-format: "v${version}"    # default: v${version}
```

Uses [Conventional Commits](https://www.conventionalcommits.org/) to determine version bumps:
- `feat:` → minor
- `fix:` / `perf:` → patch
- `BREAKING CHANGE:` → major

| Output | Description |
|--------|-------------|
| `released` | Whether a release was created |
| `version` | Released version number |
| `tag` | Git tag |

---

### setup-terraform

Setup Terraform with plugin caching, init, fmt check, and validate.

```yaml
- uses: AiFeatures/github-actions/setup-terraform@main
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
| `validate-status` | Validate exit code |

---

### cost-check

Cloud cost estimation with Infracost for Terraform changes.

```yaml
- uses: AiFeatures/github-actions/cost-check@main
  with:
    api-key: ${{ secrets.INFRACOST_API_KEY }}
    working-directory: "infra/"
    threshold-percentage: "10"   # warn if costs increase >10%
    github-token: ${{ secrets.GITHUB_TOKEN }}
```

| Output | Description |
|--------|-------------|
| `monthly-cost` | Estimated monthly cost |
| `diff-monthly-cost` | Cost difference from baseline |
| `cost-increased` | Whether cost exceeds threshold |

---

### label-pr

Auto-label pull requests based on changed file paths.

```yaml
- uses: AiFeatures/github-actions/label-pr@main
  with:
    github-token: ${{ secrets.GITHUB_TOKEN }}
    sync-labels: "true"          # remove labels when files no longer match
```

Default labels: `frontend`, `backend`, `documentation`, `tests`, `ci`, `dependencies`, `infrastructure`, `database`.

Override with custom config:

```yaml
- uses: AiFeatures/github-actions/label-pr@main
  with:
    github-token: ${{ secrets.GITHUB_TOKEN }}
    config: |
      api:
        - "src/api/**"
      mobile:
        - "apps/mobile/**"
```

| Output | Description |
|--------|-------------|
| `labels-added` | Comma-separated added labels |
| `labels-removed` | Comma-separated removed labels |

---

## Full Workflow Example

```yaml
name: CI/CD

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

permissions:
  contents: write
  pull-requests: write
  packages: write

jobs:
  ci:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: AiFeatures/github-actions/setup-node@main
        with:
          node-version: "22"
          package-manager: "pnpm"

      - name: Lint & test
        run: |
          pnpm lint
          pnpm test

      - uses: AiFeatures/github-actions/security-scan@main
        with:
          scan-type: "trivy,npm-audit"

  label:
    if: github.event_name == 'pull_request'
    runs-on: ubuntu-latest
    permissions:
      pull-requests: write
    steps:
      - uses: actions/checkout@v4
      - uses: AiFeatures/github-actions/label-pr@main
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}

  deploy-preview:
    if: github.event_name == 'pull_request'
    needs: ci
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: AiFeatures/github-actions/deploy-vercel@main
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
          vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}

  deploy-prod:
    if: github.ref == 'refs/heads/main'
    needs: ci
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: AiFeatures/github-actions/deploy-vercel@main
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
          vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}
          production: "true"

  release:
    if: github.ref == 'refs/heads/main'
    needs: deploy-prod
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0
      - uses: AiFeatures/github-actions/auto-release@main
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
```

## Contributing

1. Create a branch for your changes
2. Each action lives in its own directory with an `action.yml`
3. All actions must be composite (`using: composite`)
4. Pin third-party actions to full SHAs
5. Add tests in `.github/workflows/test.yml`
6. Open a PR — CI will validate automatically

## License

Internal use only — AiFeatures / iAiFy Enterprise.
