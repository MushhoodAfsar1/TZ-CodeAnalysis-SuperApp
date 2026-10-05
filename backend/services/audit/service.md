---
kb_section: backend
type: service
ids: [BE-SVC-AUDIT]
service: AUDIT
repo: TZ-Tigo-SuperApp-AuditLogs
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: eb87819
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-AUDIT TZ-Tigo-SuperApp-AuditLogs
**Repo:** `TZ-Tigo-SuperApp-AuditLogs` · **Type:** service · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `eb87819`
**Purpose:** Audit logs

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-AUDIT-001 | POST /api/Logs/create | LogsController.CreateLogsAsync | — | none | confirmed |


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
Status this run: **inventoried**
