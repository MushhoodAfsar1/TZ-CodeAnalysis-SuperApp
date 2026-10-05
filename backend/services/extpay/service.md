---
kb_section: backend
type: service
ids: [BE-SVC-EXTPAY]
service: EXTPAY
repo: TZ-Tigo-SuperApp-ExternalPayment
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 51718e1
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-EXTPAY Bill / government / external payments
**Repo:** `TZ-Tigo-SuperApp-ExternalPayment` · **Type:** adapter/integration · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `51718e1`
**Purpose:** Bill / government / external payments

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, RabbitMQ.Client, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-EXTPAY-001 | `POST /api/ExternalPayment/ValidateBillerDetails` | `ExternalPaymentController.ValidateBillerDetails` | ExternalPaymentController.ValidateBillerDetails | see contract | confirmed |
| BE-API-EXTPAY-002 | `POST /api/ExternalPayment/SubmitBillPayment` | `ExternalPaymentController.SubmitBillPayment` | ExternalPaymentController.SubmitBillPayment | see contract | confirmed |
| BE-API-EXTPAY-003 | `POST /api/ExternalPayment/GovernmentPaymentInquiry` | `ExternalPaymentController.GovernmentPaymentInquiry` | ExternalPaymentController.GovernmentPaymentInquiry | see contract | confirmed |
| BE-API-EXTPAY-004 | `POST /api/ExternalPayment/encrypt` | `ExternalPaymentController.Encrypt` | ExternalPaymentController.Encrypt | see contract | confirmed |
| BE-API-EXTPAY-005 | `POST /api/ExternalPayment/decrypt` | `ExternalPaymentController.Decrypt` | ExternalPaymentController.Decrypt | see contract | confirmed |
| BE-API-EXTPAY-006 | `POST /api/ExternalPayment/test` | `ExternalPaymentController.test` | ExternalPaymentController.test | see contract | confirmed |

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
| `TZExternalPaymentEFContext` / `—` | `TZTigoSuperAppExternalPayment/Domain/DBContext/TZExternalPaymentEFContext.cs` |
| `ConfigurationEFContext` / `—` | `TZTigoSuperAppExternalPayment/Domain/DBContext/ConfigurationEFContext.cs` |
| `AccountEFContext` / `—` | `TZTigoSuperAppExternalPayment/Domain/DBContext/AccountEFContext.cs` |
| `Tokens` / `—` | `TZTigoSuperAppExternalPayment/Domain/Entity/Tokens.cs` |
| `BillPayment` / `—` | `TZTigoSuperAppExternalPayment/Domain/Entity/BillPayment.cs` |
| `govpayshortcode` / `—` | `TZTigoSuperAppExternalPayment/Domain/Entity/GovPayShortCode.cs` |
| `BaseEntity` / `—` | `TZTigoSuperAppExternalPayment/Domain/Entity/BaseEntity.cs` |
| `SubmitBillPaymentRepository` / `—` | `TZTigoSuperAppExternalPayment/Domain/Repositories/SubmitBillPaymentRepository.cs` |
| `ValidateBillerDetailsRepository` / `—` | `TZTigoSuperAppExternalPayment/Domain/Repositories/ValidateBillerDetailsRepository.cs` |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`BankTransferFee`, `BankTransferPayment`, `ConfigAPIUrl`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `EnableLog:Warning`, `Encryption_Decryption_Key`, `FCMNotify`, `GovernmentInquirytoGEPG`, `IV`, `IsRedisCluster`, `MTPGBillQuery`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:LogQueueName`, `RabbitMQ:LogURL`, `RabbitMQ:QueueName`, `RabbitMQ:Username`, `RedisPassword (key name)<redacted-purpose>`, `RedisURL`, `SaveLogs`, `SendAuditLogsViaService`, `SendFCMViaService`, `SuperAppMTPGPayment`, `Tanzania:CallBackGovernmentPaymentURL`, `Tanzania:ConsumerID`, `Tanzania:MSIDN`, `Tanzania:PIN`, `Tanzania:PspCode`, `Tanzania:SysId`, `Tanzania:TerminalType`, `Tanzania:responseChanel`, `Tanzania:serviceName`, `TokenKey`, `TransactionStatus`, `is_encrypted`, `responseChanel`

## Open questions
- Gateway public URLs not in-repo.
