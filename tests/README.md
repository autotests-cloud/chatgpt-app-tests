# tests — Java autotests

Selenide + JUnit 5 + Allure 3. Student contour **REF-19** (`@Issue("REF-19")` on `tests.e2e.LoginTests`).

Target: [autotests.ai/stack](https://autotests.ai/stack/backend-java-spring/frontend-typescript-react/) + Selenoid (`multistack_prod` stand).

## Pyramid layers

| Layer | Gradle task | Package |
|-------|-------------|---------|
| unit | `testUnit` | `helpers`, `config` |
| api | `testApi` | `api` |
| e2e | `testE2e` | `tests.e2e` |
| visual | `testVisual` | `tests.visual` |

## Env profiles

Committed under `src/test/resources/config/` — `{stand}_{layer}.properties`.

| Stand | Example | baseUrl |
|-------|---------|---------|
| `multistack_ci` | `multistack_ci_e2e` | `http://localhost:8820/` |
| `multistack_prod` | `multistack_prod_e2e` | `https://autotests.ai/stack/backend-java-spring/frontend-typescript-react/` + Selenoid |

## Quick start

```bash
npm ci
./gradlew testE2e -Denv=multistack_prod_e2e \
  -DbaseUrl=https://autotests.ai/stack/backend-java-spring/frontend-typescript-react/ \
  -DapiBaseUrl=https://autotests.ai/stack/backend-java-spring/
```

Jenkins (`chatgpt-app-tests-freestyle-java-allure3-full-attachments`) runs one e2e:
`tests.e2e.LoginTests.shouldShowValidationErrorWhenUsernameIsEmpty` with full attachments.
