# Versioning Strategy

> This document mirrors the versioning strategy defined in
> [enterprise-ci-cd/VERSIONING.md](https://github.com/Ai-road-4-You/enterprise-ci-cd/blob/main/VERSIONING.md).

## How to Reference Actions

```yaml
# RECOMMENDED: Pin to major version tag
- uses: Ai-road-4-You/github-actions/setup-node@v1

# ACCEPTABLE: Pin to exact version
- uses: Ai-road-4-You/github-actions/setup-node@v1.0.0

# NOT ALLOWED in production workflows
# - uses: Ai-road-4-You/github-actions/setup-node@main
```

## Versioning Rules

All composite actions in this repository share a single version number.

| Change Type | Version Bump |
|---|---|
| Breaking change to action inputs/outputs | Major |
| New action or new backward-compatible input | Minor |
| Bug fix in existing action | Patch |

## Backward Compatibility and Deprecation

See [enterprise-ci-cd/VERSIONING.md](https://github.com/Ai-road-4-You/enterprise-ci-cd/blob/main/VERSIONING.md) for the full deprecation policy, backward compatibility rules, migration guide template, and Dependabot configuration for consumers.
