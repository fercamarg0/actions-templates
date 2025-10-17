# actions-templates

Workflows reutilizáveis (Reusable Workflows) para padronizar CI/CD entre projetos.

## 📦 Workflows Disponíveis

### 1. Python CI (`python-ci.yml`)
Lint (Ruff) + Testes (Pytest) com inputs configuráveis.

**Uso:**
```yaml
jobs:
  ci:
    uses: fercamarg0/actions-templates/.github/workflows/python-ci.yml@v2
    with:
      python-version: '3.11'
      requirements-file: 'requirements.txt'
      pytest-args: '-q'
      allow-ruff-fail: false
```

### 2. Auto PR (`auto-pr.yml`)
Criação automática de Pull Request para branches.

**Uso:**
```yaml
jobs:
  auto-pr:
    uses: fercamarg0/actions-templates/.github/workflows/auto-pr.yml@v2
```

### 3. Docker Build & Push (`docker-build-push.yml`)
Build e push de imagens Docker com suporte a multi-platform, SBOM e provenance.

**Uso:**
```yaml
jobs:
  docker:
    uses: fercamarg0/actions-templates/.github/workflows/docker-build-push.yml@v2
    with:
      registry: ghcr.io
      image-name: username/image-name
      platforms: linux/amd64,linux/arm64
    secrets:
      registry-username: ${{ github.actor }}
      registry-token: ${{ secrets.GITHUB_TOKEN }}
```

### 4. Security Scan (`security-scan.yml`)
Scans de segurança com Trivy, Dependency Review e Gitleaks.

**Uso:**
```yaml
jobs:
  security:
    uses: fercamarg0/actions-templates/.github/workflows/security-scan.yml@v2
    with:
      scan-type: fs
      severity: CRITICAL,HIGH
      fail-on-severity: high
```

### 5. Wiki Sync (`wiki-sync.yml`)
Sincronização automática de documentação para GitHub Wiki.

**Uso:**
```yaml
jobs:
  wiki:
    uses: fercamarg0/actions-templates/.github/workflows/wiki-sync.yml@v2
    with:
      sync-readme: true
      docs-path: docs
    secrets:
      wiki-token: ${{ secrets.WIKI_PUSH_TOKEN }}
```

## 🏷️ Versionamento

Use tags para fixar versões:
- `@v2` - Última versão estável
- `@main` - Desenvolvimento (pode quebrar)

## 📝 Contribuindo

1. Clone o repositório
2. Crie/modifique workflows em `.github/workflows/`
3. Teste em um repositório de exemplo
4. Crie PR com descrição das mudanças
