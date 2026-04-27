# Incidents

## Severity Levels

| Level | Name | Example | Response Time |
|-------|------|---------|---------------|
| P0 | Critical | Production down, data loss | Immediate |
| P1 | High | Core feature broken | < 1 hour |
| P2 | Medium | Non-core feature degraded | < 4 hours |
| P3 | Low | Minor bug, workaround exists | Next business day |

## Incident Response

### P0 / P1

1. **Detect** — Alert fires or user reports
2. **Communicate** — Post in `#incidents` with:
   - What is broken
   - Who is investigating
   - Estimated impact
3. **Investigate** — Identify root cause
4. **Mitigate** — Stop the bleeding (rollback, feature flag off, etc.)
5. **Fix** — Implement proper fix
6. **Verify** — Confirm resolution
7. **Postmortem** — Within 24 hours for P0, within 48 hours for P1

### Communication Template (Slack #incidents)

```
🚨 INCIDENT — P0 — Service X is down
Impact: Users cannot log in
Investigator: @dev-name
ETA: Unknown, investigating
```

Update every 15 minutes until resolved.

## Postmortem Template

Every P0 and P1 incident requires a postmortem document:

- **Summary:** One paragraph of what happened
- **Timeline:** Minute-by-minute from detection to resolution
- **Root Cause:** 5 Whys analysis
- **Impact:** Number of affected users, duration
- **What Went Well:** At least one item
- **What Went Wrong:** Honest assessment
- **Action Items:** Specific, assigned, with deadlines

Postmortems are blameless. The goal is to improve systems, not assign blame.
