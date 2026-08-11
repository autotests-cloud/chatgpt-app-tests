# tests — Java autotests

Selenide + JUnit 5 + Allure 3. Student contour **REF-19** (`@Issue("REF-19")` on `TestBase`, `ApiTestBase`, `LoginFormTests`).

Target: [reference-app.autotests.ai](https://reference-app.autotests.ai/) + Selenoid (`reference_prod` stand).

## Pyramid layers

| Layer | Gradle task | Package |
|-------|-------------|---------|
| unit | `testUnit` | `helpers`, `config` |
| api | `testApi` | `api` |
| integration | `testIntegration` | `tests.integration` |
| e2e | `testE2e` | `tests.e2e` |
| visual | `testVisual` | `tests.visual` |

## Env profiles

Committed under `src/test/resources/config/` — `{stand}_{layer}.properties`.

| Stand | Example | baseUrl |
|-------|---------|---------|
| `reference_ci` | `reference_ci_e2e` | `http://localhost:8820/` |
| `reference_prod` | `reference_prod_e2e` | `https://reference-app.autotests.ai/` + Selenoid |

## Quick start

```bash
npm ci
./gradlew testE2e -Denv=reference_prod_e2e \
  -DbaseUrl=https://reference-app.autotests.ai/ \
  -DapiBaseUrl=https://reference-app.autotests.ai/
```

Jenkins (`chatgpt-app-tests-freestyle-java-allure3-full-attachments`) runs one e2e:
`tests.e2e.LoginTests.shouldShowValidationErrorWhenUsernameIsEmpty` with full attachments.
