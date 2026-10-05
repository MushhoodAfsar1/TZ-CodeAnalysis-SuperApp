---
kb_section: backend
type: service
ids: [BE-SVC-EXTPAY]
service: EXTPAY
repo: TZ-Tigo-SuperApp-ExternalPayment
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 51718e1
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-EXTPAY TZ-Tigo-SuperApp-ExternalPayment
**Repo:** `TZ-Tigo-SuperApp-ExternalPayment` · **Type:** adapter/integration · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `51718e1`
**Purpose:** External / bill payments

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-EXTPAY-001 | POST /api/ExternalPayment | ExternalPaymentController.ValidateBillerDetails | — | none | confirmed |
| BE-API-EXTPAY-002 | POST /api/ExternalPayment | ExternalPaymentController.SubmitBillPayment | — | none | confirmed |
| BE-API-EXTPAY-003 | POST /api/ExternalPayment | ExternalPaymentController.GovernmentPaymentInquiry | — | none | confirmed |
| BE-API-EXTPAY-004 | POST /api/ExternalPayment/encrypt | ExternalPaymentController.Encrypt | — | none | confirmed |
| BE-API-EXTPAY-005 | POST /api/ExternalPayment/decrypt | ExternalPaymentController.Decrypt | — | none | confirmed |
| BE-API-EXTPAY-006 | POST /api/ExternalPayment/test | ExternalPaymentController.test | — | none | confirmed |


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
