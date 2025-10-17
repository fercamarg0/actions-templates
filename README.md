# Actions Templates

Reusable GitHub Actions workflows for standardizing CI/CD across projects.

Tested workflows ready for production use. Save configuration time and ensure consistency across your repositories.

---

## Contents
- [Why Reusable Workflows](#why-reusable-workflows)
- [Available Workflows](#available-workflows)
- [Quick Start](#quick-start)
- [Examples](#examples)
- [Contributing](#contributing)
- [License](#license)

---

## Why Reusable Workflows

Stop copying and pasting workflow configurations across repositories. Centralize tested workflows and:

- Save time: CI/CD setup in minutes
- Maintain consistency: Same standards everywhere
- Update once: Fix in one place, benefit everywhere
- Focus on code: Less configuration, more development

---

## Available Workflows

### Python CI
Automated linting with Ruff and testing with Pytest.

```yaml
uses: fercamarg0/actions-templates/.github/workflows/python-ci.yml@v2
with:
  python-version: '3.11'
  requirements-file: 'requirements.txt'
```

### Docker Build & Push
Multi-platform builds with SBOM and provenance.

```yaml
uses: fercamarg0/actions-templates/.github/workflows/docker-build-push.yml@v2
with:
  registry: ghcr.io
  image-name: ${{ github.repository }}
  platforms: linux/amd64,linux/arm64
secrets:
  registry-username: ${{ github.actor }}
  registry-token: ${{ secrets.GITHUB_TOKEN }}
```

### Security Scan
Vulnerability scanning with Trivy, Dependency Review, and Gitleaks.

```yaml
uses: fercamarg0/actions-templates/.github/workflows/security-scan.yml@v2
with:
  scan-type: fs
  severity: CRITICAL,HIGH
  fail-on-severity: high
```

### Wiki Sync
Automatic documentation synchronization to GitHub Wiki.

```yaml
uses: fercamarg0/actions-templates/.github/workflows/wiki-sync.yml@v2
with:
  sync-readme: true
secrets:
  wiki-token: ${{ secrets.WIKI_PUSH_TOKEN }}
```

### Auto PR
Automated Pull Request creation for branches.

```yaml
uses: fercamarg0/actions-templates/.github/workflows/auto-pr.yml@v2
```

---

## Quick Start

1. Choose a workflow
2. Create `.github/workflows/your-workflow.yml` in your repository
3. Copy the example and adjust parameters
4. Commit and push

**Complete Example:**

```yaml
name: CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    uses: fercamarg0/actions-templates/.github/workflows/python-ci.yml@v2
    with:
      python-version: '3.11'
      requirements-file: 'requirements.txt'
  
  security:
    uses: fercamarg0/actions-templates/.github/workflows/security-scan.yml@v2
    with:
      scan-type: fs
      severity: CRITICAL,HIGH
```

---

## Examples

See real-world usage in the [`examples/`](./examples/) directory:

- [Docker Build](./examples/docker-build.yml) - Multi-arch build and push to GHCR
- [Security Scan](./examples/security.yml) - Weekly security scanning
- [Wiki Sync](./examples/wiki.yml) - Automatic documentation sync

---

## Versioning

Use version tags for stability:

| Tag | Description | Status |
|-----|-------------|--------|
| `@v2` | Current stable | Production ready |
| `@v2.1` | Minor release | Safe to update |
| `@main` | Development | May break |

Always use tags (`@v2`) in production.

---

## Contributing

Contributions welcome. See [CONTRIBUTING.md](./CONTRIBUTING.md).

**Quick steps:**
1. Fork the repository
2. Create your feature branch
3. Test in a real repository
4. Add documentation and examples
5. Open a Pull Request

---

## License

MIT License. See [LICENSE](./LICENSE) for details.

Free to use commercially, modify, and distribute. Only requirement is keeping the copyright notice.
