# DevOps

## CI/CD Pipeline

Каждый PR запускает:

1. **Lint & Format check**
2. **Unit tests**
3. **Build Docker image**
4. **Integration tests** (в dev-окружении)
5. **Security scan** (Trivy / Snyk)

Merge в `main` триггерит автоматический деплой в **dev**.
Staging и production требуют ручного approval в GitHub Actions.

## Окружения

| Окружение | Триггер деплоя | Защита |
|-----------|---------------|--------|
| Dev | Автоматически при merge в main | Нет |
| Staging | Вручную | Требуется approval TL |
| Production | Вручную | Требуется approval TL + DevOps |

## Мониторинг

- **Dashboards:** Grafana — [ссылка](https://grafana.example.com)
- **Ключевые метрики:**
  - Error rate < 0.1%
  - P95 response time < 500мс
  - Использование CPU / Memory
- **Alerts:** PagerDuty для P0/P1 инцидентов

## Доступы

| Ресурс | Кто имеет доступ | Как запросить |
|--------|-----------------|---------------|
| Production AWS | DevOps, TL | Спросить у DevOps |
| Staging AWS | Все разработчики | Выдаётся автоматически при найме |
| CI/CD admin | DevOps, TL | Спросить у DevOps |
