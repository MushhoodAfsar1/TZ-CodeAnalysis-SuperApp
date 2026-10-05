---
kb_section: backend
type: service
ids: [BE-SVC-SESS]
service: SESS
repo: TZ-Tigo-SuperApp-Session
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 6f24061
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-SESS TZ-Tigo-SuperApp-Session
**Repo:** `TZ-Tigo-SuperApp-Session` · **Type:** auth/identity · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `6f24061`
**Purpose:** Mobile session JWT issue/refresh

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-SESS-001 | POST /api/Account | AccountController.Auth | — | anon | confirmed |
| BE-API-SESS-002 | POST /api/Account | AccountController.Refresh | — | none | confirmed |
| BE-API-SESS-003 | POST /api/Account/enc | AccountController.enc_payment | — | none | confirmed |
| BE-API-SESS-004 | POST /api/Account/decreq | AccountController.dec_req | — | none | confirmed |


## Dependencies
| Calls | Sync/Async | Why |
|---|---|---|
| Session / Account / Config (typical) | Sync HTTP | Token and profile checks |
| Called by | Sync/Async | Why |
| Mobile app / portal | Sync | User journeys |

## Data owned
| Entity / table | Purpose |
|---|---|
| See data-model.md | — |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`TokenKey`, `isEncrypted`/`is_encrypted`, `Encryption_Decryption_Key`, `IV`, `JwtExpiryMins`, `PostgresConnection` (name only)

## Open questions
Status this run: **deep-analyzed**
