# AGENTS.md

This repository is a QA automation engineering lab focused on modern web testing practices.

Main goals:
- improve Playwright automation skills
- practice API and UI testing
- build reusable automation utilities
- practice CI/CD integration
- work with Docker and Kubernetes based testing
- improve TypeScript automation architecture

Main stack:
- TypeScript
- Playwright
- API testing
- SQL
- GitHub Actions
- GitLab CI
- Docker
- Kubernetes

Project structure:
- api/ → API testing examples
- playwright/ → UI automation tests
- sql/ → SQL validation examples
- utils/ → reusable helpers
- k8s/ → Kubernetes manifests
- .github/workflows/ → CI/CD pipelines

Project rules:
- keep examples realistic for QA workflows
- prefer reusable utilities over duplicated code
- use meaningful naming
- separate UI and API logic
- keep tests readable and maintainable

Expected repository evolution:
- page object model
- API clients
- response schema validation
- fixtures and test data builders
- smoke and regression pipelines
- Docker based test execution
- GitLab CI pipelines
- Allure reporting

# ExecPlans

When writing complex features or significant refactors, use an ExecPlan (as described in .agent/PLANS.md) from design to implementation.
