# chatgpt-reference-app-tests

Java autotests for the **qaguruchatgpt** student contour — Jenkins freestyle job
[chatgpt-app-tests-freestyle-java-allure3-full-attachments](https://jenkins.qa.guru/job/chatgpt-app-tests-freestyle-java-allure3-full-attachments/).

| Link | Role |
|------|------|
| [Jira REF-19](https://jira.qa.guru/browse/REF-19) | `@Issue("REF-19")` on test bases |
| [TestOps 5329](https://allure.qa.guru/project/5329) | Launch upload (owner `qaguruchatgpt`) |
| [Confluence TZ](https://confluence.qa.guru/pages/viewpage.action?pageId=2162692) | Student task |
| Target app | [reference-app.autotests.ai](https://reference-app.autotests.ai/) |

## Layout

| Path | Role |
|------|------|
| `tests/` | Selenide + JUnit 5 + Allure 3 — Gradle pyramid (`testE2e`, `testApi`, …) |

Full reference stack (backend, frontend, deploy) lives in [autotests-ai/reference-app](https://github.com/autotests-ai/reference-app).

## Local smoke (e2e)

```bash
cd tests
npm ci
./gradlew testE2e -Denv=reference_prod_e2e \
  -DbaseUrl=https://reference-app.autotests.ai/ \
  -DapiBaseUrl=https://reference-app.autotests.ai/
```

Jenkins runs a single e2e: `tests.e2e.LoginTests.shouldShowValidationErrorWhenUsernameIsEmpty` with full Selenoid attachments.
