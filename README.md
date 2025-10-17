<div align="center">
  🇧🇷 <a href="#português">Português</a> | 🇬🇧 <a href="#english">English</a>
</div>

---

# 🔄 Actions Templates

**Workflows reutilizáveis para padronizar CI/CD em todos os seus projetos.**

Conjunto de workflows GitHub Actions testados e prontos para uso, desenvolvidos com base em experiência real de implementação. Economize horas de configuração e garanta consistência entre seus repositórios.

---

<div id="português"></div>

## Sumário
- [Por que usar workflows reutilizáveis?](#por-que-usar-workflows-reutilizáveis)
- [Workflows Disponíveis](#workflows-disponíveis)
- [Início Rápido](#início-rápido)
- [Exemplos Reais](#exemplos-reais)
- [Contribuindo](#contribuindo)
- [Licença](#licença)

---

## Por que usar workflows reutilizáveis?

Durante o desenvolvimento de projetos reais, percebi que estava **copiando e colando os mesmos workflows** entre repositórios, ajustando pequenos detalhes e perdendo tempo corrigindo bugs em múltiplos lugares. 

Este repositório nasceu dessa necessidade: **centralizar workflows testados e funcionando** para que você possa:

- ✅ **Economizar tempo**: Configure CI/CD em minutos, não horas
- ✅ **Manter consistência**: Mesmos padrões em todos os projetos
- ✅ **Atualizar uma vez**: Correções beneficiam todos os projetos automaticamente
- ✅ **Focar no código**: Menos tempo em configuração, mais tempo desenvolvendo

> 💡 **Nota**: Todos os workflows foram testados em projetos reais e seguem as melhores práticas de segurança do GitHub Actions.

---

## Workflows Disponíveis

### 🐍 Python CI
**Lint e testes automatizados com Ruff e Pytest**

Ideal para projetos Python que precisam de qualidade de código garantida.

```yaml
uses: fercamarg0/actions-templates/.github/workflows/python-ci.yml@v2
with:
  python-version: '3.11'
  requirements-file: 'requirements.txt'
```

### 🐳 Docker Build & Push
**Build multi-platform com SBOM e provenance**

Construa e publique imagens Docker com segurança integrada.

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

### 🔒 Security Scan
**Análise de vulnerabilidades com Trivy, Dependency Review e Gitleaks**

Proteja seu código contra vulnerabilidades conhecidas e secrets expostos.

```yaml
uses: fercamarg0/actions-templates/.github/workflows/security-scan.yml@v2
with:
  scan-type: fs
  severity: CRITICAL,HIGH
  fail-on-severity: high
```

### 📚 Wiki Sync
**Sincronização automática de documentação para GitHub Wiki**

Mantenha sua documentação sempre atualizada sem esforço manual.

```yaml
uses: fercamarg0/actions-templates/.github/workflows/wiki-sync.yml@v2
with:
  sync-readme: true
secrets:
  wiki-token: ${{ secrets.WIKI_PUSH_TOKEN }}
```

### 🔄 Auto PR
**Criação automática de Pull Requests**

Automatize a criação de PRs para branches específicas.

```yaml
uses: fercamarg0/actions-templates/.github/workflows/auto-pr.yml@v2
```

---

## Início Rápido

1. **Escolha um workflow** da lista acima
2. **Crie um arquivo** `.github/workflows/seu-workflow.yml` no seu repositório
3. **Copie o exemplo** e ajuste os parâmetros
4. **Commit e push** - o workflow estará ativo!

### Exemplo Completo

Veja como configurar CI completo para um projeto Python:

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
      pytest-args: '-v'
  
  security:
    uses: fercamarg0/actions-templates/.github/workflows/security-scan.yml@v2
    with:
      scan-type: fs
      severity: CRITICAL,HIGH
```

---

## Exemplos Reais

Quer ver os workflows em ação? Confira os exemplos na pasta [`examples/`](./examples/):

- **[Docker Build](./examples/docker-build.yml)**: Build e push para GHCR com múltiplas arquiteturas
- **[Security Scan](./examples/security.yml)**: Scan completo de segurança com schedule semanal
- **[Wiki Sync](./examples/wiki.yml)**: Sincronização automática de docs para Wiki

---

## Versionamento

Este repositório segue [Semantic Versioning](https://semver.org/):

| Tag | Descrição | Recomendação |
|-----|-----------|--------------|
| `@v2` | Versão estável atual | ✅ **Use em produção** |
| `@v2.1` | Minor release | ✅ Seguro para atualizar |
| `@main` | Branch de desenvolvimento | ⚠️ Pode quebrar |

**Dica**: Sempre use tags (`@v2`) em produção para garantir estabilidade.

---

## Contribuindo

Contribuições são bem-vindas! Este projeto existe para ser útil à comunidade.

**Como contribuir**:
1. 🍴 Fork o repositório
2. 🔨 Crie sua feature branch: `git checkout -b feat/nova-feature`
3. ✅ Teste seu workflow em um repositório de exemplo
4. 📝 Adicione documentação e exemplos
5. 🚀 Abra um Pull Request

Veja o guia completo em [CONTRIBUTING.md](./CONTRIBUTING.md).

---

## Licença

Este projeto é distribuído sob a licença MIT, o que significa que você pode:

- ✅ Usar comercialmente
- ✅ Modificar como quiser
- ✅ Distribuir livremente
- ✅ Usar em projetos privados

A única exigência é manter o aviso de copyright. Veja [LICENSE](./LICENSE) para detalhes.

---

<div align="center">

**Made with ❤️ by [Fernando Camargo](https://github.com/fercamarg0)**

⭐ Se este projeto foi útil, considere dar uma estrela!

</div>

---

<div id="english"></div>

# 🇬🇧 English

## Actions Templates

**Reusable workflows to standardize CI/CD across all your projects.**

A collection of tested and production-ready GitHub Actions workflows, built from real-world implementation experience. Save hours of configuration and ensure consistency across your repositories.

### Quick Links

- [Why use reusable workflows?](#why-use-reusable-workflows)
- [Available Workflows](#available-workflows-1)
- [Quick Start](#quick-start-1)
- [Contributing](#contributing-1)

---

### Why use reusable workflows?

Stop copying and pasting the same workflow configurations across repositories. Centralize your CI/CD logic and benefit from:

- ⚡ **Time savings**: Set up CI/CD in minutes
- 🔄 **Consistency**: Same standards across all projects
- 🔧 **Easy updates**: Fix once, benefit everywhere
- 🎯 **Focus**: Less config, more coding

### Available Workflows

| Workflow | Description | Use Case |
|----------|-------------|----------|
| **Python CI** | Ruff + Pytest | Python projects |
| **Docker Build** | Multi-platform builds | Container apps |
| **Security Scan** | Trivy + Gitleaks | Security checks |
| **Wiki Sync** | Auto documentation | Wiki updates |
| **Auto PR** | Automated PRs | Branch management |

### Quick Start

1. Choose a workflow from the list
2. Create `.github/workflows/your-workflow.yml`
3. Copy the example and adjust parameters
4. Commit and push - you're done!

**Example**:

```yaml
jobs:
  ci:
    uses: fercamarg0/actions-templates/.github/workflows/python-ci.yml@v2
    with:
      python-version: '3.11'
```

### Contributing

Contributions welcome! See [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

### License

MIT License - See [LICENSE](./LICENSE) for details.

---

<div align="center">

**[⬆ Back to top](#-actions-templates)**

</div>
