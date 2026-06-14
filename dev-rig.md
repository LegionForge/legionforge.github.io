---
layout: product
title: dev-rig
tagline: Shared CI workflows and audit harness for LegionForge projects
subtagline: one set of reusable workflows across every repo — lint, test, SAST, audit, secrets, SBOM, Trivy
description: >-
  dev-rig is the shared CI/CD substrate used across every LegionForge repo.
  Reusable GitHub Actions workflows, pre-commit configuration, and a single-
  command audit harness.
permalink: /dev-rig/
category: tool
product_id: dev-rig
repo: dev-rig
---

## What it is

dev-rig is the **shared CI/CD substrate** used across every LegionForge repo. It provides:

- **Reusable GitHub Actions workflows** — lint, test, SAST, dependency audit, secrets scan, SBOM generation, container scan (Trivy)
- **Pre-commit configuration** — Black, isort, ruff, mypy, bandit, detect-secrets
- **Audit harness** — Bandit + pip-audit + URI scrubbing, runnable as a single make target

The goal is that every project under the LegionForge org has the same security / quality baseline without copy-pasting workflow files between repos.

## Using it in a project

```yaml
# .github/workflows/ci.yml
name: CI
on: [pull_request, push]

jobs:
  lint:    { uses: LegionForge/dev-rig/.github/workflows/lint.yml@main }
  test:    { uses: LegionForge/dev-rig/.github/workflows/test.yml@main }
  sast:    { uses: LegionForge/dev-rig/.github/workflows/sast.yml@main }
  audit:   { uses: LegionForge/dev-rig/.github/workflows/audit.yml@main }
  secrets: { uses: LegionForge/dev-rig/.github/workflows/secrets.yml@main }
  sbom:    { uses: LegionForge/dev-rig/.github/workflows/sbom.yml@main }
```

That's the entire CI config — every workflow is sourced from dev-rig. Updating dev-rig updates the CI across all projects that reference `@main`.

## When to use it outside LegionForge

If you maintain multiple Python repos and want a consistent security baseline, dev-rig is a reasonable template. The workflows are MIT-licensed and the configuration is intentionally vanilla — they don't assume LegionForge-specific structure.

## Status

Active. Public. See the [GitHub repo](https://github.com/LegionForge/dev-rig) for the latest.
