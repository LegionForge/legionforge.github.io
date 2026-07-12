---
layout: product
title: dev-rig
tagline: Shared CI workflows and audit harness for LegionForge projects
subtagline: reusable workflows and local audits for Python, static, and mixed-language repos
description: >-
  dev-rig is the shared CI/CD substrate used across LegionForge repos.
  Reusable GitHub Actions workflows, pre-commit configuration, and a single-
  command audit harness.
permalink: /dev-rig/
category: tool
product_id: dev-rig
repo: dev-rig
---

## What it is

dev-rig is the **shared CI/CD substrate** used across LegionForge repos. It provides:

- **Reusable GitHub Actions workflows** — lint, test, SAST, dependency audit, secrets scan, SBOM generation, container scan (Trivy)
- **Pre-commit configuration** — ruff, mypy, bandit, ShellCheck, OSV Scanner, and gitleaks
- **Audit harness** — Python checks when applicable, OSV Scanner, gitleaks, ShellCheck, Semgrep packs, and LegionForge risky-exec rules

The goal is that every project under the LegionForge org has a clear security / quality baseline without copy-pasting workflow files between repos.

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

That's the entire CI config for a Python project — every workflow is sourced from dev-rig. Updating dev-rig updates the CI across all projects that reference `@main`.

## Local audit

```bash
LegionForge-dev-rig/scripts/audit.sh /path/to/repo
```

The harness is repo-shape aware. Python checks run when Python files or dependency manifests exist. Static sites still receive the applicable checks: OSV Scanner, gitleaks working-tree/history scans, ShellCheck when shell scripts exist, Semgrep packs when Docker is available, and the LegionForge risky-exec rules.

## When to use it outside LegionForge

If you maintain multiple Python repos and want a consistent security baseline, dev-rig is a reasonable template. The workflows are MIT-licensed and the configuration is intentionally vanilla — they don't assume LegionForge-specific structure.

## Status

Active. Public. See the [GitHub repo](https://github.com/LegionForge/dev-rig) for the latest, and the [project security inventory](https://docs.legionforge.org/security/project-inventory/) for current coverage across repos.
