# Development

## Git Workflow

We use **trunk-based development**:

- `main` is always deployable
- All work happens on short-lived feature branches
- Branch naming: `feat/description`, `fix/description`, `docs/description`
- Pull Requests are mandatory for all changes

## Code Style

- We use the linters configured in the repository (ESLint, Prettier, Black, etc.)
- Run `npm run lint` or equivalent before pushing
- Pre-commit hooks are configured — they will block commits with style violations

## Code Review

- Every PR requires **at least 1 approval** before merge
- Turnaround target: review within **4 hours** during work hours
- As a reviewer, check:
  - Logic correctness
  - Test coverage
  - Security implications
  - Performance impact (for hot paths)

## Commits

Use [Conventional Commits](https://www.conventionalcommits.org/):

```
feat: add user authentication
fix: resolve login redirect loop
docs: update API examples
refactor: simplify payment processing
```

## Pull Requests

PR description template (auto-populated):

```markdown
## What
Brief description of the change

## Why
Business or technical reason

## How to Test
Steps to verify the change

## Screenshots (if UI change)
```
