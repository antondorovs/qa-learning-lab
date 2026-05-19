# Project Decisions

## Push Strategy

The repository is mirrored to both GitHub and GitLab.

Decision: completed work should be pushed to both remotes when the user approves pushing.

```bash
git push origin main
git push gitlab main
```

## UI Test Stability

Problem: UI tests that depended directly on `example.com` and `iana.org` passed locally but failed or became unstable in CI.

Decision: UI smoke tests should use Playwright route mocks for external demo pages. This keeps browser tests fast and stable in GitHub/GitLab CI.

## Environment Variables

Problem: local `.env` is ignored by git, so CI did not have the same values as local runs.

Decision:

- Keep safe public practice values in `.env.example`.
- Provide safe defaults in `utils/env.ts`.
- Define CI env vars explicitly in GitHub Actions and GitLab CI.

## Language Statistics

Goal: improve GitHub language visibility for the user's QA stack.

Decision:

- Add useful examples in JavaScript, TypeScript, SQL, YAML, Docker, and Kubernetes.
- Avoid meaningless filler code.
- Use `.gitattributes` to keep generated HTML reports out of language statistics.

## Commit Style

Decision: prefer clear, small-to-medium commits with practical messages, such as:

- `Fix CI environment for Playwright tests`
- `Stabilize UI tests for CI`
- `Add QA infrastructure examples and fix UI checks`

Before committing, Codex should summarize changed files and test results.
