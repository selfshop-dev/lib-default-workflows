# .github

Организационный репозиторий [selfshop-dev](https://github.com/selfshop-dev) с общими настройками, шаблонами и reusable workflows для всех Go-библиотек.

## Что не наследуется

Эти файлы должны лежать в каждом репозитории отдельно:

| Файл | Почему |
|---|---|
| `.github/workflows/*.yml` | GitHub не наследует workflows между репо |
| `codecov.yml` | Применяется только из корня конкретного репо |
| `codeql.yml` | Конфиг CodeQL читается локально во время анализа |
| `dependabot.yml` | Настраивается индивидуально под каждый репо |
| `.golangci.yml` | Линтер читает конфиг из рабочей директории |

## Reusable Workflows

Workflows из этого репо можно вызывать из любого репозитория организации через `workflow_call`.

### CI

```yaml
# .github/workflows/ci.yml
jobs:
  ci:
    uses: selfshop-dev/.github/.github/workflows/ci.yml@main
    secrets: inherit  # пробрасывает все секреты организации в другие репо
```

### Security (Trivy)

```yaml
# .github/workflows/security.yml
jobs:
  security:
    uses: selfshop-dev/.github/.github/workflows/security.yml@main
```

### CodeQL

```yaml
# .github/workflows/codeql.yml
jobs:
  codeql:
    uses: selfshop-dev/.github/.github/workflows/codeql.yml@main
```

## Лицензия

[MIT](LICENSE) © 2026 selfshop-dev