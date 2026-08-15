# Page objects

**autotests-ai-multistack-app** — home page at app root. Resolved via `baseUrl` in `config/multistack_ci_*.properties`.

| Page | Class | Open |
|------|-------|------|
| Home | `HomePage` | `open("")` → `GET /` |
| Login | `LoginPage` | `open("/login")` |

Post-auth state (welcome message, logout) lives on `HomePage` at `/`.

## Profiles

`multistack_ci_e2e.properties` / `multistack_ci_integration.properties`: `baseUrl=http://localhost:8820/`
