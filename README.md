# chatgpt-app-tests

Java autotests for the **qaguruchatgpt** student contour — Jenkins freestyle job
[chatgpt-app-tests-freestyle-java-allure3-full-attachments](https://jenkins.qa.guru/job/chatgpt-app-tests-freestyle-java-allure3-full-attachments/).

| Link | Role |
|------|------|
| [Jira REF-19](https://jira.qa.guru/browse/REF-19) | `@Issue("REF-19")` on test bases |
| [TestOps 5329](https://allure.qa.guru/project/5329) | Launch upload (owner `qaguruchatgpt`) |
| [Confluence TZ](https://confluence.qa.guru/pages/viewpage.action?pageId=2162692) | Student task |
| Target app | [autotests.ai/stack](https://autotests.ai/stack/backend-java-spring/frontend-typescript-react/) |

## Layout

| Path | Role |
|------|------|
| `tests/` | Selenide + JUnit 5 + Allure 3 — Gradle pyramid (`testE2e`, `testApi`, …) |

Full etalon stack (backend, frontend, deploy) lives in [autotests-ai/autotests-ai-multistack-app](https://github.com/autotests-ai/autotests-ai-multistack-app).

## Local smoke (e2e)

```bash
cd tests
npm ci
./gradlew testE2e -Denv=multistack_prod_e2e \
  -DbaseUrl=https://autotests.ai/stack/backend-java-spring/frontend-typescript-react/ \
  -DapiBaseUrl=https://autotests.ai/stack/backend-java-spring/
```

Jenkins runs a single e2e: `tests.e2e.LoginTests.shouldShowValidationErrorWhenUsernameIsEmpty` with full Selenoid attachments.
