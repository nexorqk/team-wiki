# DevOps

## CI/CD Pipeline

Every PR triggers:

1. **Lint & Format check**
2. **Unit tests**
3. **Build Docker image**
4. **Integration tests** (on dev environment)
5. **Security scan** (Trivy / Snyk)

Merges to `main` trigger automatic deployment to **dev**.
Staging and production require manual approval in GitHub Actions.

## Environments

| Environment | Deploy Trigger | Protection |
|-------------|---------------|------------|
| Dev | Auto on merge to main | None |
| Staging | Manual | TL approval |
| Production | Manual | TL + DevOps approval |

## Monitoring

- **Dashboards:** Grafana — [link](https://grafana.example.com)
- **Key Metrics:**
  - Error rate < 0.1%
  - P95 response time < 500ms
  - CPU / Memory utilization
- **Alerts:** PagerDuty for P0/P1 incidents

## Access

| Resource | Who Has Access | How to Request |
|----------|---------------|----------------|
| Production AWS | DevOps, TL | Ask DevOps |
| Staging AWS | All engineers | Auto-granted on hire |
| CI/CD admin | DevOps, TL | Ask DevOps |
