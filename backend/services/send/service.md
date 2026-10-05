---
kb_section: backend
type: service
ids: [BE-SVC-SEND]
service: SEND
repo: TZ-Tigo-SuperApp-SendMoney
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 599771b
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-SEND TZ-Tigo-SuperApp-SendMoney
**Repo:** `TZ-Tigo-SuperApp-SendMoney` · **Type:** service · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `599771b`
**Purpose:** Send money / P2P

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-SEND-001 | POST /api/SendMoney | SendMoneyController.VerifySendMoney | — | none | confirmed |
| BE-API-SEND-002 | POST /api/SendMoney | SendMoneyController.TransferSendMoney | — | none | confirmed |
| BE-API-SEND-003 | POST /api/SendMoney | SendMoneyController.GetTopFiveGiftTransaction | — | none | confirmed |
| BE-API-SEND-004 | POST /api/SendMoney | SendMoneyController.GetGift | — | none | confirmed |
| BE-API-SEND-005 | POST /api/SendMoney/encVerify | SendMoneyController.encVerify | — | none | confirmed |
| BE-API-SEND-006 | POST /api/SendMoney/encTransfer | SendMoneyController.encTransfer | — | none | confirmed |
| BE-API-SEND-007 | POST /api/StandingOrder | StandingOrderController.ScheduleOrder | — | none | confirmed |
| BE-API-SEND-008 | POST /api/StandingOrder | StandingOrderController.GetOrderList | — | none | confirmed |
| BE-API-SEND-009 | POST /api/StandingOrder | StandingOrderController.GetOrderHistory | — | none | confirmed |
| BE-API-SEND-010 | POST /api/StandingOrder | StandingOrderController.DeleteOrder | — | none | confirmed |
| BE-API-SEND-011 | POST /api/StandingOrder | StandingOrderController.GetOrdersByDateRange | — | none | confirmed |
| BE-API-SEND-012 | POST /api/StandingOrder | StandingOrderController.PauseOrder | — | none | confirmed |
| BE-API-SEND-013 | POST /api/StandingOrder | StandingOrderController.ResumeOrder | — | none | confirmed |
| BE-API-SEND-014 | POST /api/ATMCashout | ATMCashoutController.ATMCashoutBankList | — | none | confirmed |
| BE-API-SEND-015 | POST /api/ATMCashout | ATMCashoutController.ATMCashoutGenerateOtp | — | none | confirmed |


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
