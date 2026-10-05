---
kb_section: backend
type: service
ids: [BE-SVC-AIRTIME]
service: AIRTIME
repo: TZ-Tigo-SuperApp-AirTimeTopup
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 7a52359
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-AIRTIME TZ-Tigo-SuperApp-AirTimeTopup
**Repo:** `TZ-Tigo-SuperApp-AirTimeTopup` · **Type:** service · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `7a52359`
**Purpose:** Airtime top-up

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-AIRTIME-001 | POST /api/FiberProduct | FiberProductController.GetReferenceNumberValidation | — | none | confirmed |
| BE-API-AIRTIME-002 | POST /api/FiberProduct | FiberProductController.SubmitPayment | — | none | confirmed |
| BE-API-AIRTIME-003 | POST /api/FiberProduct | FiberProductController.SubmitPaymentCapacityChange | — | none | confirmed |
| BE-API-AIRTIME-004 | POST /api/FiberProduct | FiberProductController.GetReferenceNumberCapacityChange | — | none | confirmed |
| BE-API-AIRTIME-005 | POST /api/AirTime | AirTimeController.AirTimeTopUp | — | none | confirmed |
| BE-API-AIRTIME-006 | POST /api/AirTime | AirTimeController.AirTimeTopUpV1 | — | none | confirmed |
| BE-API-AIRTIME-007 | POST /api/AirTime | AirTimeController.VerifySendMoney | — | none | confirmed |
| BE-API-AIRTIME-008 | POST /api/AirTime | AirTimeController.AirTimeTopUpOthers | — | none | confirmed |
| BE-API-AIRTIME-009 | POST /api/AirTime/enc | AirTimeController.enc | — | none | confirmed |
| BE-API-AIRTIME-010 | POST /api/AirTime/dec | AirTimeController.dec | — | none | confirmed |


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
