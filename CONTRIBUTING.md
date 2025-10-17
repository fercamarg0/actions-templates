# Contributing to actions-templates

Obrigado por considerar contribuir com actions-templates! 🎉

## Como Contribuir

### Reportar Bugs ou Sugerir Features

1. Verifique se já existe uma issue similar
2. Crie uma nova issue com:
   - **Bug**: Descrição clara, steps para reproduzir, comportamento esperado vs atual
   - **Feature**: Descrição do caso de uso, benefícios esperados

### Contribuir com Código

1. **Fork** o repositório
2. **Clone** seu fork localmente
3. **Crie uma branch** para sua feature/fix:
   ```bash
   git checkout -b feat/nome-da-feature
   ```
4. **Faça suas alterações**:
   - Siga as convenções de código existentes
   - Teste seus workflows em um repositório de teste
   - Adicione exemplos de uso em `examples/`
5. **Commit** com mensagens claras (Conventional Commits):
   ```
   feat: adicionar workflow de terraform
   fix: corrigir cache do docker build
   docs: atualizar README com exemplo de kubernetes
   ```
6. **Push** para seu fork
7. **Abra um Pull Request** com:
   - Descrição clara das mudanças
   - Referência a issues relacionadas
   - Exemplos de uso do novo workflow

## Diretrizes para Workflows

### Estrutura de um Workflow Reutilizável

```yaml
name: Nome Descritivo (Reusable)

on:
  workflow_call:
    inputs:
      param-name:
        description: "Descrição clara do parâmetro"
        required: true/false
        type: string
        default: "valor-padrao"  # se não for required
    secrets:
      secret-name:
        description: "Descrição clara do secret"
        required: true/false

jobs:
  job-name:
    runs-on: ubuntu-latest
    permissions:  # Sempre especifique as permissões mínimas necessárias
      contents: read
    steps:
      - uses: actions/checkout@v4  # Use sempre as versões mais recentes
      # ... resto dos steps
```

### Boas Práticas

1. **Inputs bem documentados**:
   - Sempre adicione `description`
   - Use `required: false` com `default` quando apropriado
   - Tipos corretos (`string`, `boolean`, `number`)

2. **Secrets seguros**:
   - Nunca faça echo/print de secrets
   - Use `required: true` apenas se realmente necessário

3. **Permissões mínimas**:
   - Especifique explicitamente as `permissions` necessárias
   - Use `contents: read` como padrão
   - Adicione `write` apenas quando necessário

4. **Versões fixas**:
   - Use versões específicas de actions: `@v4`, `@v3`
   - Prefira SHA commits para máxima segurança em produção

5. **Cache inteligente**:
   - Use cache do GitHub Actions quando aplicável
   - Cache de dependências, build artifacts, etc.

6. **Outputs úteis**:
   - Exponha informações úteis como outputs do job
   - Documente os outputs no README

### Testando Workflows

Antes de submeter um PR, teste seu workflow em um repositório de teste:

1. Crie um repositório de teste
2. Adicione o workflow que usa seu template:
   ```yaml
   uses: SEU_USUARIO/actions-templates/.github/workflows/SEU_WORKFLOW.yml@SUA_BRANCH
   ```
3. Teste diferentes combinações de inputs
4. Verifique logs de execução
5. Confirme que funciona em PRs, pushes, etc.

### Exemplos

Sempre adicione um exemplo em `examples/`:

```yaml
# examples/seu-workflow.yml
name: Exemplo de Uso

on: [push, pull_request]

jobs:
  exemplo:
    uses: fercamarg0/actions-templates/.github/workflows/seu-workflow.yml@v2
    with:
      input1: valor1
      input2: valor2
    secrets:
      secret1: ${{ secrets.SECRET1 }}
```

## Code Review

Todos os PRs passam por code review. Buscamos:

- ✅ Código limpo e bem documentado
- ✅ Workflows testados e funcionando
- ✅ README atualizado com novo workflow
- ✅ Exemplo de uso adicionado
- ✅ Sem hardcoded values ou secrets expostos
- ✅ Permissões mínimas necessárias
- ✅ Compatibilidade com versões anteriores (quando aplicável)

## Versionamento

Seguimos [Semantic Versioning](https://semver.org/):

- **v2.0.0**: Breaking changes (incompatível com v1)
- **v2.1.0**: Novos features (compatível com v2.0)
- **v2.1.1**: Bug fixes (compatível com v2.1)

## Dúvidas?

Abra uma issue ou discussion no GitHub!

---

**Código de Conduta**: Todos os contribuidores devem seguir nosso [Code of Conduct](CODE_OF_CONDUCT.md).
