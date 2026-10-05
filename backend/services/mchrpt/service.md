---
kb_section: backend
type: service
ids: [BE-SVC-MCHRPT]
service: MCHRPT
repo: TZ-Tigo-SuperApp-MChangoReportScheduler
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 34ba77f
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-MCHRPT TZ-Tigo-SuperApp-MChangoReportScheduler
**Repo:** `TZ-Tigo-SuperApp-MChangoReportScheduler` · **Type:** batch/scheduler · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `34ba77f`
**Purpose:** MChango report jobs

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| — | — | — | no HTTP controllers | — | — |


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
