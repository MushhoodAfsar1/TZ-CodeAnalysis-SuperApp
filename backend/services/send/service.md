---
kb_section: backend
type: service
ids: [BE-SVC-SEND]
service: SEND
repo: TZ-Tigo-SuperApp-SendMoney
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 599771b
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-SEND P2P send money, standing orders, ATM cash-out
**Repo:** `TZ-Tigo-SuperApp-SendMoney` · **Type:** service · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `599771b`
**Purpose:** P2P send money, standing orders, ATM cash-out

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** MassTransit.RabbitMQ, Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-SEND-001 | `POST /api/StandingOrder/ScheduleOrder` | `StandingOrderController.ScheduleOrder` | StandingOrderController.ScheduleOrder | see contract | confirmed |
| BE-API-SEND-002 | `POST /api/StandingOrder/GetOrderList` | `StandingOrderController.GetOrderList` | StandingOrderController.GetOrderList | see contract | confirmed |
| BE-API-SEND-003 | `POST /api/StandingOrder/GetOrderHistory` | `StandingOrderController.GetOrderHistory` | StandingOrderController.GetOrderHistory | see contract | confirmed |
| BE-API-SEND-004 | `POST /api/StandingOrder/DeleteOrder` | `StandingOrderController.DeleteOrder` | StandingOrderController.DeleteOrder | see contract | confirmed |
| BE-API-SEND-005 | `POST /api/StandingOrder/GetOrdersByDateRange` | `StandingOrderController.GetOrdersByDateRange` | StandingOrderController.GetOrdersByDateRange | see contract | confirmed |
| BE-API-SEND-006 | `POST /api/StandingOrder/PauseOrder` | `StandingOrderController.PauseOrder` | StandingOrderController.PauseOrder | see contract | confirmed |
| BE-API-SEND-007 | `POST /api/StandingOrder/ResumeOrder` | `StandingOrderController.ResumeOrder` | StandingOrderController.ResumeOrder | see contract | confirmed |
| BE-API-SEND-008 | `POST /api/ATMCashout/GetATMCashoutBankList` | `ATMCashoutController.ATMCashoutBankList` | ATMCashoutController.ATMCashoutBankList | see contract | confirmed |
| BE-API-SEND-009 | `POST /api/ATMCashout/ATMCashoutGenerateOtp` | `ATMCashoutController.ATMCashoutGenerateOtp` | ATMCashoutController.ATMCashoutGenerateOtp | see contract | confirmed |
| BE-API-SEND-010 | `POST /api/SendMoney/VerifySendMoney` | `SendMoneyController.VerifySendMoney` | SendMoneyController.VerifySendMoney | see contract | confirmed |
| BE-API-SEND-011 | `POST /api/SendMoney/TransferSendMoney` | `SendMoneyController.TransferSendMoney` | SendMoneyController.TransferSendMoney | see contract | confirmed |
| BE-API-SEND-012 | `POST /api/SendMoney/GetTopFiveGiftTransaction` | `SendMoneyController.GetTopFiveGiftTransaction` | SendMoneyController.GetTopFiveGiftTransaction | see contract | confirmed |
| BE-API-SEND-013 | `POST /api/SendMoney/GetGift` | `SendMoneyController.GetGift` | SendMoneyController.GetGift | see contract | confirmed |
| BE-API-SEND-014 | `POST /api/SendMoney/encVerify` | `SendMoneyController.encVerify` | SendMoneyController.encVerify | see contract | confirmed |
| BE-API-SEND-015 | `POST /api/SendMoney/encTransfer` | `SendMoneyController.encTransfer` | SendMoneyController.encTransfer | see contract | confirmed |

## Dependencies
| Calls | Sync/Async | Why |
|---|---|---|
| CONFIG `CMM` / `ConfigAPIUrl` | Sync | response-code mapping, catalogues |

| Called by | Sync/Async | Why |
|---|---|---|
| Mobile app (direct or via external gateway) | Sync | product APIs |
| WebPortal | Sync | admin screens (IDENT/CONFIG mainly) |

## Data owned
| Entity / table | Purpose |
|---|---|
| `TZAccountEFContext` / `—` | `TZTigoSuperAppSendMoney/Domain/DBContext/TZAccountEFContext.cs` |
| `TZSendMoneyEFContext` / `—` | `TZTigoSuperAppSendMoney/Domain/DBContext/TZSendMoneyEFContext.cs` |
| `StandingOrder` / `—` | `TZTigoSuperAppSendMoney/Domain/Entity/StandingOrder.cs` |
| `BaseEntity` / `—` | `TZTigoSuperAppSendMoney/Domain/Entity/BaseEntity.cs` |
| `Transfer` / `—` | `TZTigoSuperAppSendMoney/Domain/Entity/SendMoney/Transfer.cs` |
| `ATMTransactions` / `—` | `TZTigoSuperAppSendMoney/Domain/Entity/SendMoney/ATMTransactions.cs` |
| `giftmoneyrecord` / `—` | `TZTigoSuperAppSendMoney/Domain/Entity/SendMoney/giftmoneyrecord.cs` |
| `tanqrshortcode` / `—` | `TZTigoSuperAppSendMoney/Domain/Entity/SendMoney/tanqrshortcode.cs` |
| `Profile` / `—` | `TZTigoSuperAppSendMoney/Domain/Entity/Account/Profile.cs` |
| `standingordermapping` / `—` | `TZTigoSuperAppSendMoney/Domain/Entity/Account/StandingOrderMapping.cs` |
| `Tokens` / `—` | `TZTigoSuperAppSendMoney/Domain/Entity/Account/Tokens.cs` |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`ATMCashout:<redacted-purpose>`, `ATMCashout:CashoutBankList`, `ATMCashout:CashoutGenerateOtp`, `ATMCashout:GetToken`, `ATMCashout:Grant_Type`, `ATMCashout:Username`, `ConfigAPIUrl`, `DeleteOrderApiUrl`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `Encryption_Decryption_Key`, `FCMNotify`, `GetCustomerIdApiUrl`, `GetOrderHistoryApiUrl`, `GetOrderListApiUrl`, `GetOrdersByDateRangeApiUrl`, `GetTokenApiUrl`, `IV`, `MchangoNotfication`, `PauseOrderApiUrl`, `PaymentType`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:IsHttpsRabbitMQ`, `RabbitMQ:LogQueueName`, `RabbitMQ:LogURL`, `RabbitMQ:Port`, `RabbitMQ:QueueName`, `RabbitMQ:Username`, `RedisURL`, `ResumeOrderApiUrl`, `SaveLogs`, `ScheduleOrderApiUrl`, `SendAuditLogsViaService`, `SendFCMViaService`, `StandingOrderApiKey`, `TANQR`, `Tanzania:ConsumerID`, `Tanzania:ConsumerId`, `Tanzania:MSIDN`

## Open questions
- Gateway public URLs not in-repo.
