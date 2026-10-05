---
kb_section: backend
type: service
ids: [BE-SVC-SAVING]
service: SAVING
repo: TZ-Tigo-SuperApp-Saving
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 2ca8791
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-SAVING Personal savings / Kibubu+
**Repo:** `TZ-Tigo-SuperApp-Saving` · **Type:** service · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `2ca8791`
**Purpose:** Personal savings / Kibubu+

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, RabbitMQ.Client, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-SAVING-001 | `POST /api/Saving/SubscriptionStatus` | `SavingController.SubscriptionStatus` | SavingController.SubscriptionStatus | see contract | confirmed |
| BE-API-SAVING-002 | `POST /api/Saving/enc` | `SavingController.enc` | SavingController.enc | see contract | confirmed |
| BE-API-SAVING-003 | `POST /api/KibubuPlus/GetEligiblePlans` | `KibubuPlusController.GetEligiblePlans` | KibubuPlusController.GetEligiblePlans | see contract | confirmed |
| BE-API-SAVING-004 | `POST /api/KibubuPlus/ActivatePlan` | `KibubuPlusController.ActivatePlan` | KibubuPlusController.ActivatePlan | see contract | confirmed |
| BE-API-SAVING-005 | `POST /api/KibubuPlus/CheckBalance` | `KibubuPlusController.CheckBalance` | KibubuPlusController.CheckBalance | see contract | confirmed |
| BE-API-SAVING-006 | `POST /api/KibubuPlus/ManualContribution` | `KibubuPlusController.ManualContribution` | KibubuPlusController.ManualContribution | see contract | confirmed |
| BE-API-SAVING-007 | `POST /api/KibubuPlus/Withdraw` | `KibubuPlusController.Withdraw` | KibubuPlusController.Withdraw | see contract | confirmed |
| BE-API-SAVING-008 | `POST /api/KibubuPlus/SavingHistory` | `KibubuPlusController.SavingHistory` | KibubuPlusController.SavingHistory | see contract | confirmed |

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
| `SavingTransactions` / `SavingTransactions` | `TZTigoSuperAppSaving/Data/Entities/SavingTransactions.cs` |
| `BaseEntity` / `—` | `TZTigoSuperAppSaving/Data/Entities/BaseEntity.cs` |
| `SubscriptionRepository` / `—` | `TZTigoSuperAppSaving/Domain/Repositories/SubscriptionRepository.cs` |
| `KibubuPlusRepository` / `—` | `TZTigoSuperAppSaving/Domain/Repositories/KibubuPlusRepository.cs` |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`ConfigAPIUrl`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `EnableLog:Warning`, `Encryption_Decryption_Key`, `FCMNotify`, `IV`, `IsRedisCluster`, `KibubuPlus:ActivatePlanUrl`, `KibubuPlus:BasicToken`, `KibubuPlus:CheckBalanceUrl`, `KibubuPlus:GetEligiblePlansUrl`, `KibubuPlus:ManualContributionUrl`, `KibubuPlus:SavingHistoryUrl`, `KibubuPlus:TokenUrl`, `KibubuPlus:WithdrawUrl`, `MFSUserDetails`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:LogQueueName`, `RabbitMQ:LogURL`, `RabbitMQ:QueueName`, `RabbitMQ:Username`, `RedisPassword (key name)<redacted-purpose>`, `RedisURL`, `SaveLogs`, `SendAuditLogsViaService`, `SendFCMViaService`, `SubscriptionStatusUrl`, `Tanzania:<redacted-purpose>`, `Tanzania:Account:UserName`, `Tanzania:ConsumerID`, `Tanzania:Subscription`, `Tanzania:Withdraw`, `Tanzania:responseChanel`, `Tanzania:serviceName`, `Tanzania:sourceMSISDN`, `Tanzania:sourcePIN`, `TokenKey`, `is_encrypted`

## Open questions
- Gateway public URLs not in-repo.
