# Releases

## Release Checklist

### Pre-Release (Day Before)

- [ ] All tickets for the release are merged to `main`
- [ ] QA has signed off on staging
- [ ] Release notes are drafted
- [ ] Database migrations are reviewed by DevOps

### Release Day

- [ ] Run automated E2E suite against staging
- [ ] Deploy to production (manual approval in GitHub Actions)
- [ ] Run smoke tests on production
- [ ] Monitor error rate for 30 minutes
- [ ] Announce release in `#releases` Slack channel

### Post-Release

- [ ] Merge release tag back to `main` if needed
- [ ] Archive released tickets

## Ownership

- **Release Manager:** Rotates weekly (schedule in team calendar)
- **Release Manager responsibilities:**
  - Coordinate what goes into the release
  - Run the checklist
  - Be the first responder if something goes wrong

## Hotfixes

If a critical bug is found in production:

1. Create branch from latest production tag: `git checkout -b hotfix/description`
2. Fix and test locally
3. Open PR with `hotfix:` prefix — expedited review
4. Merge and deploy immediately after 1 approval
5. Post-incident review within 24 hours

## Rollback

If a release causes issues:

1. Immediate: Re-deploy previous stable Docker image
2. Within 1 hour: Decide between fix-forward or full rollback
3. Database migrations: consult DevOps before rollback
