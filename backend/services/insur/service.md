---
kb_section: backend
type: service
ids: [BE-SVC-INSUR]
service: INSUR
repo: TZ-Tigo-SuperApp-Insurrance
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 38747da
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-INSUR TZ-Tigo-SuperApp-Insurrance
**Repo:** `TZ-Tigo-SuperApp-Insurrance` · **Type:** service · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `38747da`
**Purpose:** Insurance

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-INSUR-001 | POST /api/Conversion/encGetVehicleDetails | ConversionController.encGetVehicleDetails | — | none | confirmed |
| BE-API-INSUR-002 | POST /api/Conversion/encGetMotorVehicleDetails | ConversionController.encGetMotorVehicleDetails | — | none | confirmed |
| BE-API-INSUR-003 | POST /api/Conversion/encConfirmVehicleRegistration | ConversionController.encConfirmVehicleRegistration | — | none | confirmed |
| BE-API-INSUR-004 | POST /api/Conversion/encGetQuote | ConversionController.encGetQuote | — | none | confirmed |
| BE-API-INSUR-005 | POST /api/Conversion/encMTPGBillQuery | ConversionController.encMTPGBillQuery | — | none | confirmed |
| BE-API-INSUR-006 | POST /api/Conversion/encPaymentNotification | ConversionController.encPaymentNotification | — | none | confirmed |
| BE-API-INSUR-007 | POST /api/Insurance | InsuranceController.GetVehicleDetails | — | none | confirmed |
| BE-API-INSUR-008 | POST /api/Insurance | InsuranceController.GetMotorVehicleDetails | — | none | confirmed |
| BE-API-INSUR-009 | POST /api/Insurance | InsuranceController.ConfirmVehicleRegistration | — | none | confirmed |
| BE-API-INSUR-010 | POST /api/Insurance | InsuranceController.GetQuote | — | none | confirmed |
| BE-API-INSUR-011 | POST /api/Insurance | InsuranceController.GetQuoteV1 | — | none | confirmed |
| BE-API-INSUR-012 | POST /api/Insurance | InsuranceController.MTPGBillQuery | — | none | confirmed |
| BE-API-INSUR-013 | POST /api/Insurance | InsuranceController.PaymentNotification | — | none | confirmed |


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
