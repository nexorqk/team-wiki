# Testing

## Test Pyramid

| Level | Responsibility | When to Run |
|-------|---------------|-------------|
| Unit tests | Developers | On every PR, locally and in CI |
| Integration tests | Developers + QA | On every PR in CI |
| E2E tests | QA team | Nightly + before release |

## Bug Reports

When you find a bug, create a ticket with:

- **Title:** Clear, one-sentence description
- **Steps to Reproduce:** Numbered list
- **Expected Result:** What should happen
- **Actual Result:** What actually happens
- **Environment:** Browser, OS, app version
- **Severity:**
  - **Blocker** — prevents core functionality, no workaround
  - **Critical** — major functionality broken, workaround exists
  - **Major** — noticeable issue, limited impact
  - **Minor** — cosmetic or edge case

## Environments

| Environment | Purpose | Data |
|-------------|---------|------|
| Local | Development | Mock / seeded |
| Dev | Integration testing | Synthetic |
| Staging | Pre-release validation | Anonymized production |
| Production | Live users | Real |

## Regression Testing

- QA runs full regression before every release
- Critical paths are covered by automated E2E tests
- New features must include test cases in the ticket before development starts
