---
kb_section: backend
type: service
ids: [BE-SVC-WALLET]
service: WALLET
repo: TZ-Tigo-SuperApp-Wallet
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 27737b1
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-WALLET Wallet balance and cash-out
**Repo:** `TZ-Tigo-SuperApp-Wallet` · **Type:** service · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `27737b1`
**Purpose:** Wallet balance and cash-out

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** Dapper, MassTransit.RabbitMQ, Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, Serilog, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, Serilog.Sinks.Console, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-WALLET-001 | `POST /api/CashOut/cashOutFee` | `CashOutController.CashOutFee` | CashOutController.CashOutFee | see contract | confirmed |
| BE-API-WALLET-002 | `POST /api/CashOut/cashOutPaymentV1` | `CashOutController.CashOutPaymentV1` | CashOutController.CashOutPaymentV1 | see contract | confirmed |
| BE-API-WALLET-003 | `POST /api/CashOut/cashOutPayment` | `CashOutController.CashOutPayment` | CashOutController.CashOutPayment | see contract | confirmed |
| BE-API-WALLET-004 | `POST /api/CashOut/encrypt` | `CashOutController.Encrypt` | CashOutController.Encrypt | see contract | confirmed |
| BE-API-WALLET-005 | `POST /api/CashOut/decrypt` | `CashOutController.Decrypt` | CashOutController.Decrypt | see contract | confirmed |
| BE-API-WALLET-006 | `POST /api/WalletBalance/GetBalance` | `WalletBalanceController.GetBalance` | WalletBalanceController.GetBalance | see contract | confirmed |
| BE-API-WALLET-007 | `POST /api/WalletBalance/enc` | `WalletBalanceController.enc` | WalletBalanceController.enc | see contract | confirmed |

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
| `AppplicationContext` / `—` | `TZTigoSuperAppWallet/Domain/AppplicationContext.cs` |
| `ConnectionStringOptions` / `—` | `TZTigoSuperAppWallet/Domain/AppplicationContext.cs` |
| `FTContext` / `—` | `TZTigoSuperAppWallet/Domain/DBContext/FTContext.cs` |
| `AccountEFContext` / `—` | `TZTigoSuperAppWallet/Domain/DBContext/AccountEFContext.cs` |
| `RepositoryContext` / `—` | `TZTigoSuperAppWallet/Domain/DBContext/RepositoryContext.cs` |
| `ConfigurationManagementClient` / `—` | `TZTigoSuperAppWallet/Domain/Repositories/ConfigurationManagementClient.cs` |
| `WalletBalanceRepository` / `—` | `TZTigoSuperAppWallet/Domain/Repositories/WalletBalanceRepository.cs` |
| `Token` / `—` | `TZTigoSuperAppWallet/Domain/RequestModels/Token.cs` |
| `RequestModel` / `—` | `TZTigoSuperAppWallet/Domain/RequestModels/RequestModel.cs` |
| `RestAPIRequest` / `—` | `TZTigoSuperAppWallet/Domain/Models/GenericModel/RestAPIRequest.cs` |
| `AuditLogsRequest` / `—` | `TZTigoSuperAppWallet/Domain/Models/GenericModel/AuditLogsRequest.cs` |
| `cashoutpayment` / `—` | `TZTigoSuperAppWallet/Domain/Models/Entities/cashoutpayment.cs` |
| `Tokens` / `—` | `TZTigoSuperAppWallet/Domain/Models/Entities/Tokens.cs` |
| `BaseEntity` / `—` | `TZTigoSuperAppWallet/Domain/Models/Entities/BaseEntity.cs` |
| `ResponseCodeRequest` / `—` | `TZTigoSuperAppWallet/Domain/Models/ResponseCode/ResponseCodeRequest.cs` |
| `ResponseCodeResponse` / `—` | `TZTigoSuperAppWallet/Domain/Models/ResponseCode/ResponseCodeResponse.cs` |
| `MTPGGetBalanceResponse` / `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/GetBalance/MTPGGetBalanceResponse.cs` |
| `WalletApiResponse` / `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/GetBalance/MTPGGetBalanceResponse.cs` |
| `GetBalanceRequest` / `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/GetBalance/GetBalanceRequest.cs` |
| `CashOutFeeResponseDto` / `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/CashOutFee/CashOutFeeResponseDto.cs` |
| `ParameterType` / `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/CashOutFee/CashOutFeeResponseDto.cs` |
| `CashOutFeeRequestDto` / `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/CashOutFee/CashOutFeeRequestDto.cs` |
| `creditParty` / `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/CashOutFee/CashOutFeeRequestDto.cs` |
| `FCMTemplates` / `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/Enum/FCMTemplates.cs` |
| `StringEnum` / `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/Enum/FCMTemplates.cs` |
| `CashOutPaymentRequestDto` / `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/CashOutPayment/CashOutPaymentRequestDto.cs` |
| `CashOutPaymentResponseDto` / `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/CashOutPayment/CashOutPaymentResponseDto.cs` |
| `FCMNotificationRequest` / `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/FCMNotification/FCMNotificationRequest.cs` |
| `NotificationTemplate` / `—` | `TZTigoSuperAppWallet/Domain/Models/WalletManagementModels/FCMNotification/FCMNotificationRequest.cs` |
| `EncryptedRequest` / `—` | `TZTigoSuperAppWallet/Domain/Models/GenericModel/Request/EncryptedRequest.cs` |
| `BaseRequest` / `—` | `TZTigoSuperAppWallet/Domain/Models/GenericModel/Request/BaseRequest.cs` |
| `BaseResponse` / `—` | `TZTigoSuperAppWallet/Domain/Models/GenericModel/Response/BaseResponse.cs` |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`CashOutFee`, `CashOutPayment`, `ConfigAPIUrl`, `ConnectionStrings:<redacted-purpose>`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `EnableLog:Warning`, `Encryption_Decryption_Key`, `FCMNotify`, `IV`, `IsRedisCluster`, `MTPGGetBalance`, `Origins`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:LogQueueName`, `RabbitMQ:LogURL`, `RabbitMQ:QueueName`, `RabbitMQ:Username`, `RedisPassword (key name)<redacted-purpose>`, `RedisURL`, `SendFCMViaService`, `Tanzania:<redacted-purpose>`, `Tanzania:ChannelUser`, `Tanzania:ChannerPass`, `Tanzania:ConsumerID`, `Tanzania:TerminalType`, `Tanzania:Username`, `Tanzania:responseChanel`, `Tanzania:serviceName`, `TokenKey`, `isEncrypted`, `responseChanel`

## Open questions
- Gateway public URLs not in-repo.
