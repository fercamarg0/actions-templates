# actions-templates

Workflows reutilizáveis (Reusable Workflows) para padronizar CI/CD entre projetos.

- `.github/workflows/python-ci.yml`: Lint (Ruff) + Testes (Pytest). Inputs configuráveis via `workflow_call`.
- `.github/workflows/auto-pr.yml`: Criação automática de PR para branches via `workflow_call`.

Exemplo de uso em outro repositório:

```yaml
name: CI
on: [push, pull_request]
jobs:
  call-reusable-ci:
    uses: fercamarg0/actions-templates/.github/workflows/python-ci.yml@main
    with:
      python-version: '3.11'
      requirements-file: 'requirements.txt'
      pytest-args: '-q'
      allow-ruff-fail: false
```
