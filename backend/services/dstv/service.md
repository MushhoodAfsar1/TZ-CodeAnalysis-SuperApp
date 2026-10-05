---
kb_section: backend
type: service
ids: [BE-SVC-DSTV]
service: DSTV
repo: TZ-Tigo-SuperApp-DigitalSubscription
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: fd31aa1
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-DSTV TZ-Tigo-SuperApp-DigitalSubscription
**Repo:** `TZ-Tigo-SuperApp-DigitalSubscription` · **Type:** service · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `fd31aa1`
**Purpose:** Digital subscriptions

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-DSTV-001 | POST /api/DSTV | DSTVController.GetCustomerDetail | — | none | confirmed |
| BE-API-DSTV-002 | POST /api/DSTV | DSTVController.GetDueAmount | — | none | confirmed |
| BE-API-DSTV-003 | POST /api/DSTV | DSTVController.GetAvailableProducts | — | none | confirmed |
| BE-API-DSTV-004 | POST /api/DSTV | DSTVController.SubmitPaymentBySmartcard | — | none | confirmed |
| BE-API-DSTV-005 | POST /api/DSTV | DSTVController.PaymentConfirmation | — | none | confirmed |
| BE-API-DSTV-006 | POST /api/DSTV/CustomerDetailenc | DSTVController.CustomerDetailenc | — | none | confirmed |
| BE-API-DSTV-007 | POST /api/DSTV/DueAmountenc | DSTVController.DueAmountenc | — | none | confirmed |


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
