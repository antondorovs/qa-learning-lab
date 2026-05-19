# AGENTS.md

Project instructions for Codex and future AI-assisted work in this repository.

## Project Overview

`qa-learning-lab` is a personal QA engineering practice repository. It is used to build and demonstrate practical skills in:

- UI automation
- API testing
- SQL practice
- CI/CD configuration
- Docker and Kubernetes basics
- QA documentation, utilities, and reporting examples

The repository should grow as a useful QA learning lab and portfolio project. Do not add meaningless filler code only for GitHub statistics.

## Tech Stack

- TypeScript
- JavaScript
- Playwright
- SQL
- Node.js
- dotenv
- Docker
- Kubernetes
- GitHub Actions
- GitLab CI
- Jenkins
- YAML

## Project Structure

- `api/` - API tests, API client helpers, payloads, schemas, and API utilities.
- `playwright/` - UI tests, page objects, fixtures, and browser automation examples.
- `sql/` - SQL practice datasets, QA reporting queries, window functions, and health checks.
- `utils/` - reusable QA helpers, metrics, quality gates, test data builders, and environment config.
- `.github/workflows/` - GitHub Actions workflows.
- `.gitlab-ci.yml` - GitLab CI pipeline.
- `k8s/` - Kubernetes manifests.
- `docker/` - Docker runner examples.
- `bug-reports/`, `test-cases/`, `notes/` - manual QA documentation areas.
- `.agent/` - Codex project memory, ExecPlan guidance, decisions, commands, and active task notes.
- `docs/` - human-facing documentation that is broader than one source folder.

## Key Commands

Install dependencies:

```bash
npm ci
```

Install Playwright browsers locally when needed:

```bash
npx playwright install --with-deps
```

Run all tests:

```bash
npm test
```

Run all tests in Chromium:

```bash
npm run test:chromium
```

Run API tests:

```bash
npm run test:api -- --project=chromium
```

Run UI tests:

```bash
npm run test:ui -- --project=chromium
```

Run tests headed:

```bash
npm run test:headed
```

Open Playwright report:

```bash
npm run test:report
```

Build/run with Docker Compose:

```bash
docker compose up --build
```

## Environment

- Local `.env` is ignored by git.
- `.env.example` contains safe public practice values.
- CI workflows define the same public practice values explicitly:
  - `BASE_URL=https://reqres.in`
  - `API_EMAIL=eve.holt@reqres.in`
  - `API_PASSWORD=cityslicka`

Do not commit real secrets.

## Code Rules

- Keep examples practical and relevant to QA learning.
- Prefer small, focused changes over broad rewrites.
- Follow existing Playwright patterns and local helper structure.
- Keep API test helpers reusable and readable.
- Keep UI tests stable in CI.
- Avoid external-site dependency in UI tests when a Playwright route mock is enough.
- API tests may use public practice APIs when that is the intent of the example.
- Keep generated reports out of git:
  - `playwright-report/`
  - `test-results/`
  - `coverage/`
- Do not commit `node_modules/`.
- Keep Markdown clear and portfolio-friendly.
- Use ASCII unless the file already needs non-ASCII content.

## CI Rules

GitHub Actions:

- Main workflow: `.github/workflows/playwright.yml`
- API smoke workflow: `.github/workflows/api-smoke.yml`
- CI command for full checks: `npm run test:chromium`

GitLab CI:

- Pipeline file: `.gitlab-ci.yml`
- Use the official Playwright image for browser jobs:
  - `mcr.microsoft.com/playwright:v1.59.1-noble`

UI tests should be stable without relying on `example.com` or IANA being reachable from the CI runner. Use Playwright fixtures and `page.route` mocks for public demo pages.

## Self-Check Instructions

Before committing code changes:

```bash
git status --short
git diff --stat
```

For test-related changes, run the relevant tests:

```bash
npm run test:chromium
```

Or, for focused checks:

```bash
npm run test:api -- --project=chromium
npm run test:ui -- --project=chromium
```

After test runs, confirm:

- Failed tests are understood and fixed or explicitly documented.
- `test-results/` and `playwright-report/` are not staged.
- No secrets are staged.
- New files support the QA learning purpose.
- CI config remains consistent between GitHub and GitLab when applicable.

## ExecPlans

When writing complex features or significant refactors, use an ExecPlan (as described in `.agent/PLANS.md`) from design to implementation.

## Git And Remotes

This project is mirrored to both GitHub and GitLab.

- GitHub remote: `origin`
- GitLab remote: `gitlab`

When the user approves pushing completed work, push to both:

```bash
git push origin main
git push gitlab main
```

## Collaboration Rules

- Explain what files will be changed before editing.
- Show or summarize `git status --short`, `git diff --stat`, and test results before committing.
- Do not push large changes without user confirmation.
- Keep the user involved because this repository is also a learning tool.
- When a new session starts, read this file first, then inspect `README.md` and the project memory files in `.agent/`.
- Current project memory files live in `.agent/PROJECT_CONTEXT.md`, `.agent/TASKS.md`, `.agent/DECISIONS.md`, and `.agent/COMMANDS.md`.
