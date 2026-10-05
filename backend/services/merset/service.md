---
kb_section: backend
type: service
ids: [BE-SVC-MERSET]
service: MERSET
repo: TZ-Tigo-SuperApp-MerchantSettlementScheduler
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: d638213
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-MERSET Merchant settlement scheduler
**Repo:** `TZ-Tigo-SuperApp-MerchantSettlementScheduler` · **Type:** batch/scheduler · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `d638213`
**Purpose:** Merchant settlement scheduler

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, RabbitMQ.Client, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|

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
| `BaseEntity` / `—` | `TZTigoSuperAppMerchantSettlementScheduler/Domain/BaseEntity.cs` |
| `EntityDetailRequest` / `—` | `TZTigoSuperAppMerchantSettlementScheduler/Data/RequestModel/EntityDetailRequest.cs` |
| `EntityDetailResponse` / `—` | `TZTigoSuperAppMerchantSettlementScheduler/Data/ResponseModel/EntityDetailResponse.cs` |
| `ResponseMapEntity` / `—` | `TZTigoSuperAppMerchantSettlementScheduler/Data/ResponseModel/EntityDetailResponse.cs` |
| `ResponseData` / `—` | `TZTigoSuperAppMerchantSettlementScheduler/Data/ResponseModel/EntityDetailResponse.cs` |
| `EntityOfficerDetails` / `—` | `TZTigoSuperAppMerchantSettlementScheduler/Data/ResponseModel/EntityDetailResponse.cs` |
| `EntityDocumentDetails` / `—` | `TZTigoSuperAppMerchantSettlementScheduler/Data/ResponseModel/EntityDetailResponse.cs` |
| `EntityDetail` / `—` | `TZTigoSuperAppMerchantSettlementScheduler/Data/ResponseModel/EntityDetailResponse.cs` |
| `OtherDetails` / `—` | `TZTigoSuperAppMerchantSettlementScheduler/Data/ResponseModel/EntityDetailResponse.cs` |
| `EntityAddressDetails` / `—` | `TZTigoSuperAppMerchantSettlementScheduler/Data/ResponseModel/EntityDetailResponse.cs` |
| `EntityContactDetails` / `—` | `TZTigoSuperAppMerchantSettlementScheduler/Data/ResponseModel/EntityDetailResponse.cs` |
| `TZMerchantContext` / `—` | `TZTigoSuperAppMerchantSettlementScheduler/Domain/DBContext/TZMerchantContext.cs` |
| `scheduleSubscriber` / `—` | `TZTigoSuperAppMerchantSettlementScheduler/Domain/Entities/ScheduleSubscriber.cs` |
| `transaction` / `—` | `TZTigoSuperAppMerchantSettlementScheduler/Domain/Entities/Transaction.cs` |
| `schedule` / `—` | `TZTigoSuperAppMerchantSettlementScheduler/Domain/Entities/Schedule.cs` |
| `BillPayment` / `—` | `TZTigoSuperAppMerchantSettlementScheduler/Domain/Entities/BillPayment.cs` |
| `TransferSchedule` / `—` | `TZTigoSuperAppMerchantSettlementScheduler/Domain/Entities/TransferSchedule.cs` |
| `OperationType` / `—` | `TZTigoSuperAppMerchantSettlementScheduler/Domain/Enum/OperationType.cs` |
| `FCMTemplates` / `—` | `TZTigoSuperAppMerchantSettlementScheduler/Domain/Enum/FCMTemplates.cs` |
| `StringEnum` / `—` | `TZTigoSuperAppMerchantSettlementScheduler/Domain/Enum/FCMTemplates.cs` |
| `SettlementScheduleRepository` / `—` | `TZTigoSuperAppMerchantSettlementScheduler/Domain/Repositories/SettlementScheduleRepository.cs` |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`ConfigAPIUrl`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `EnableLog:Warning`, `Encryption_Decryption_Key`, `FCMNotify`, `IV`, `IsRedisCluster`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:IsHttpsRabbitMQ`, `RabbitMQ:LogURL`, `RabbitMQ:Port`, `RabbitMQ:QueueName`, `RabbitMQ:URL`, `RabbitMQ:Username`, `RedisPassword (key name)<redacted-purpose>`, `RedisURL`, `SendFCMViaService`, `Tanzania:BankTransferFee`, `Tanzania:BankTransferPayment`, `Tanzania:BankTransferShortCode`, `Tanzania:ChannelPass`, `Tanzania:ChannelUser`, `Tanzania:ConsumerID`, `Tanzania:FeeSourcePIN`, `Tanzania:FeeTerminalType`, `Tanzania:MaxRecord`, `Tanzania:PaymentTerminalType`, `Tanzania:PaymentType`, `Tanzania:PaymentTypeProxy`, `Tanzania:ServiceDelayTimeMin`, `Tanzania:ShortCode`, `Tanzania:SuperAppMTPGBillQuery`, `Tanzania:SuperAppMTPGGetBalance`, `Tanzania:SuperAppMTPGPayment`, `Tanzania:TerminalType`, `TokenKey`, `is_encrypted`, `responseChanel`

## Open questions
- Gateway public URLs not in-repo.
