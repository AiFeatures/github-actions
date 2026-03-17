# Changelog

All notable changes to the github-actions composite actions will be documented in this file.

This project adheres to [Semantic Versioning](https://semver.org/) and uses
[semantic-release](https://github.com/semantic-release/semantic-release) for automated releases.

## [1.0.0] - 2026-03-15

### Added

- Initial release of 13 composite actions
- setup-node: Node.js setup with pnpm/npm/yarn caching
- setup-python: Python setup with pip/poetry/uv caching
- setup-terraform: Terraform setup with caching and validation
- docker-build-push: Docker build and push to GHCR
- security-scan: Trivy, npm audit, secret scanning
- auto-release: Semantic versioning with changelog
- cost-check: Infracost cost estimation
- verify-attestation: Verify artifact attestations
- label-pr: Auto-label pull requests
- notify-slack: Slack notification for build status
- deploy-vercel: Deploy to Vercel
- deploy-fly: Deploy to Fly.io
- deploy-railway: Deploy to Railway
- deploy-supabase: Deploy Supabase migrations
- deploy-firebase: Deploy to Firebase
