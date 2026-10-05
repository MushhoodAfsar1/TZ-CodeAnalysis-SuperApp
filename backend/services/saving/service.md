---
kb_section: backend
type: service
ids: [BE-SVC-SAVING]
service: SAVING
repo: TZ-Tigo-SuperApp-Saving
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 2ca8791
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-SAVING TZ-Tigo-SuperApp-Saving
**Repo:** `TZ-Tigo-SuperApp-Saving` · **Type:** service · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `2ca8791`
**Purpose:** Savings

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-SAVING-001 | POST /api/Saving | SavingController.SubscriptionStatus | — | none | confirmed |
| BE-API-SAVING-002 | POST /api/Saving/enc | SavingController.enc | — | none | confirmed |
| BE-API-SAVING-003 | POST /api/KibubuPlus | KibubuPlusController.GetEligiblePlans | — | none | confirmed |
| BE-API-SAVING-004 | POST /api/KibubuPlus | KibubuPlusController.ActivatePlan | — | none | confirmed |
| BE-API-SAVING-005 | POST /api/KibubuPlus | KibubuPlusController.CheckBalance | — | none | confirmed |
| BE-API-SAVING-006 | POST /api/KibubuPlus | KibubuPlusController.ManualContribution | — | none | confirmed |
| BE-API-SAVING-007 | POST /api/KibubuPlus | KibubuPlusController.Withdraw | — | none | confirmed |
| BE-API-SAVING-008 | POST /api/KibubuPlus | KibubuPlusController.SavingHistory | — | none | confirmed |


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
