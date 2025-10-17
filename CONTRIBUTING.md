# Contributing

Thank you for considering contributing to actions-templates.

## How to Contribute

### Report Bugs or Suggest Features

1. Check if a similar issue already exists
2. Create a new issue with:
   - **Bug**: Clear description, steps to reproduce, expected vs actual behavior
   - **Feature**: Use case description, expected benefits

### Contributing Code

1. Fork the repository
2. Clone your fork locally
3. Create a branch:
   ```bash
   git checkout -b feat/feature-name
   ```
4. Make your changes:
   - Follow existing code conventions
   - Test workflows in a test repository
   - Add usage examples in `examples/`
5. Commit with clear messages (Conventional Commits):
   ```
   feat: add terraform workflow
   fix: fix docker build cache
   docs: update README with kubernetes example
   ```
6. Push to your fork
7. Open a Pull Request with:
   - Clear description of changes
   - Reference to related issues
   - Usage examples

## Workflow Guidelines

### Reusable Workflow Structure

```yaml
name: Descriptive Name (Reusable)

on:
  workflow_call:
    inputs:
      param-name:
        description: "Clear parameter description"
        required: true/false
        type: string
        default: "default-value"  # if not required
    secrets:
      secret-name:
        description: "Clear secret description"
        required: true/false

jobs:
  job-name:
    runs-on: ubuntu-latest
    permissions:  # Always specify minimum required permissions
      contents: read
    steps:
      - uses: actions/checkout@v4  # Always use latest versions
      # ... other steps
```

### Best Practices

1. **Well-documented inputs**:
   - Always add `description`
   - Use `required: false` with `default` when appropriate
   - Correct types (`string`, `boolean`, `number`)

2. **Secure secrets**:
   - Never echo/print secrets
   - Use `required: true` only when necessary

3. **Minimum permissions**:
   - Explicitly specify required `permissions`
   - Use `contents: read` as default
   - Add `write` only when needed

4. **Fixed versions**:
   - Use specific action versions: `@v4`, `@v3`
   - Prefer SHA commits for maximum security

5. **Smart caching**:
   - Use GitHub Actions cache when applicable
   - Cache dependencies, build artifacts, etc.

6. **Useful outputs**:
   - Expose useful information as job outputs
   - Document outputs in README

### Testing Workflows

Before submitting a PR, test your workflow in a test repository:

1. Create a test repository
2. Add workflow using your template:
   ```yaml
   uses: YOUR_USER/actions-templates/.github/workflows/YOUR_WORKFLOW.yml@YOUR_BRANCH
   ```
3. Test different input combinations
4. Check execution logs
5. Confirm it works on PRs, pushes, etc.

### Examples

Always add an example in `examples/`:

```yaml
# examples/your-workflow.yml
name: Usage Example

on: [push, pull_request]

jobs:
  example:
    uses: fercamarg0/actions-templates/.github/workflows/your-workflow.yml@v2
    with:
      input1: value1
      input2: value2
    secrets:
      secret1: ${{ secrets.SECRET1 }}
```

## Code Review

All PRs go through code review. We look for:

- Clean and well-documented code
- Tested and working workflows
- Updated README with new workflow
- Usage example added
- No hardcoded values or exposed secrets
- Minimum required permissions
- Backward compatibility (when applicable)

## Versioning

We follow [Semantic Versioning](https://semver.org/):

- **v2.0.0**: Breaking changes (incompatible with v1)
- **v2.1.0**: New features (compatible with v2.0)
- **v2.1.1**: Bug fixes (compatible with v2.1)

## Questions?

Open an issue or discussion on GitHub.

---

**Code of Conduct**: All contributors must follow our [Code of Conduct](CODE_OF_CONDUCT.md).
