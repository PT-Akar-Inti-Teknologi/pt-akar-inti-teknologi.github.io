---
layout: default
title: Release Versioning
permalink: /standards/repository/release
parent: Code Repository
grand_parent: Standards
nav_order: 6
---

# Release Versioning

## Why

Consistent release versioning:
- Helps track changes between releases
- Allows CI/CD automation (e.g., changelog, deployment)
- Provides clear context for rollback, support, and compatibility
- Supports semantic understanding of backward compatibility

## Versioning Format

We follow **Semantic Versioning (SemVer)** with optional pre-release identifiers:

```
v<MAJOR>.<MINOR>.<PATCH>[-<LABEL>.<BUILD>]
```

### Examples
- `v1.0.0`
- `v2.3.1`
- `v3.4.0-beta.2`
- `v2.5.0-rc.1`

## SemVer Rules

| Segment     | Purpose                                                                 |
|-------------|-------------------------------------------------------------------------|
| MAJOR       | Incompatible or breaking changes                                        |
| MINOR       | Backward-compatible feature additions                                   |
| PATCH       | Backward-compatible bug fixes or enhancements                          |
| LABEL       | Pre-release tag (e.g., `alpha`, `beta`, `rc`)                           |
| BUILD       | Incremental build or iteration number for that pre-release             |

## Tagging Policy

- Use prefix `v` (e.g., `v1.0.0`) to distinguish tags from branches
- Tags must always point to a commit in the `main` or `staging` branch
- For pre-release (alpha, beta, rc), only tag from `staging`
- For production releases, only tag from `main`

## Tag Naming Examples

| Context                    | Tag Name         | Description                                 |
|----------------------------|------------------|---------------------------------------------|
| First stable release       | `v1.0.0`         | First official release                      |
| Patch fix for bug          | `v1.0.1`         | Minor fix, backward-compatible              |
| Feature update             | `v1.1.0`         | Minor update with new features              |
| Breaking schema changes    | `v2.0.0`         | Major version bump                          |
| Beta testing round 2       | `v2.1.0-beta.2`  | Second beta release for v2.1.0              |
| Release candidate          | `v1.3.0-rc.1`    | First release candidate before stable       |

## GitHub/GitLab Notes

- Tags will trigger deployment pipelines based on your CI/CD rules
- Use annotated tags (`git tag -a`) if possible for clearer history
- Maintain changelog based on commits between tags (e.g., using `standard-version` or `semantic-release`)

## Tools Recommendation

- [`semantic-release`](https://semantic-release.gitbook.io/) for automatic versioning and tagging based on commit messages
- [`standard-version`](https://github.com/conventional-changelog/standard-version) for manual but structured version bumping
