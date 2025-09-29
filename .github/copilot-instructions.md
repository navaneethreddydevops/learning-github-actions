# GitHub Actions Learning Repository - AI Agent Instructions

## Project Purpose
This repository is designed for learning GitHub Actions concepts, patterns, and best practices. The focus is on creating practical, educational workflows that demonstrate various GitHub Actions capabilities.

## Repository Structure
```
.github/
├── workflows/          # GitHub Actions workflow files (.yml/.yaml)
└── copilot-instructions.md
```

## Development Guidelines

### Workflow Creation Patterns
- **Naming Convention**: Use descriptive names like `ci-python-app.yml`, `deploy-to-staging.yml`, `learn-basic-workflow.yml`
- **Trigger Strategy**: Include common triggers (`push`, `pull_request`, `workflow_dispatch`) for learning purposes
- **Job Organization**: Structure jobs logically (build → test → deploy) with clear dependencies
- **Environment Variables**: Use repository secrets and environment variables to demonstrate secure practices

### Learning-Focused Approaches
- **Progressive Complexity**: Start with basic workflows (hello world, simple CI) before advanced patterns
- **Documentation**: Include inline comments in workflows explaining each step and action
- **Multiple Examples**: Create variations of similar workflows to show different approaches
- **Error Handling**: Demonstrate both success and failure scenarios with appropriate error handling

### Python Integration
Based on `.gitignore`, Python workflows are expected:
- Use `actions/setup-python@v4` for Python environment setup
- Include common Python tools: `pip`, `pytest`, `black`, `flake8`, `mypy`
- Demonstrate testing with multiple Python versions using matrix strategies
- Show package building and publishing workflows

### Workflow File Structure
```yaml
name: Descriptive Workflow Name
on: [push, pull_request, workflow_dispatch]
jobs:
  job-name:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Upload artifacts (use v4+)
        uses: actions/upload-artifact@v4  # v3 deprecated as of April 2024
        with:
          name: artifact-name
          path: path/to/artifact
      - name: Download artifacts (use v4+)
        uses: actions/download-artifact@v4  # v3 deprecated as of April 2024
        with:
          name: artifact-name
```

### Key Learning Areas to Cover
- **Basic CI/CD**: Build, test, deploy cycles
- **Matrix Builds**: Testing across multiple environments/versions
- **Conditional Logic**: Using `if:` conditions and expressions
- **Secrets Management**: Safe handling of API keys and credentials
- **Artifact Handling**: Uploading/downloading build artifacts (always use v4+ actions)
- **Caching**: Optimizing workflow performance with caching strategies
- **Custom Actions**: Creating reusable actions
- **Environment Deployments**: Using GitHub environments for staged deployments

### Commands and Scripts
- Create workflows: Place `.yml` files in `.github/workflows/`
- Test locally: Use `act` tool or GitHub CLI for local testing when possible
- Validate syntax: Use GitHub's workflow syntax checker
- Monitor runs: Check Actions tab for execution results and logs

### Action Version Requirements
- **Artifact Actions**: ALWAYS use `actions/upload-artifact@v4` and `actions/download-artifact@v4`
  - v3 was deprecated in April 2024 and will cause workflow failures
  - v4 introduces breaking changes in artifact handling behavior
- **Checkout Action**: Use `actions/checkout@v4` for latest Git features
- **Setup Actions**: Use latest versions (`actions/setup-python@v4`, `actions/setup-node@v4`, etc.)

### Dependencies and Integrations
- **External Services**: Demonstrate integration with common services (Docker Hub, AWS, etc.)
- **Third-party Actions**: Use popular marketplace actions with proper version pinning
- **Security**: Follow security best practices for action usage and secret management

## Example Workflow Starters
When creating new workflows, consider these templates:
- **Basic CI**: Checkout → Setup → Install → Test → Report
- **Release**: Trigger on tag → Build → Test → Package → Publish
- **Deploy**: Trigger on main branch → Build → Test → Deploy to staging/production
- **Scheduled**: Cron-based workflows for maintenance tasks

## Best Practices for Learning
- Always include `workflow_dispatch` trigger for manual testing
- Use descriptive step names that explain the learning objective
- Add comments explaining GitHub Actions concepts and syntax
- Create both simple and complex examples of the same concept
- Include examples of common failures and how to debug them
- **Version Awareness**: Always use current action versions to avoid deprecation errors
  - Check GitHub's changelog for deprecation notices
  - Update workflows when actions are deprecated (e.g., artifact actions v3 → v4)
