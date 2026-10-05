---
kb_section: backend
type: service
ids: [BE-SVC-AIRTIME]
service: AIRTIME
repo: TZ-Tigo-SuperApp-AirTimeTopup
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 7a52359
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-AIRTIME Airtime and fiber product top-up
**Repo:** `TZ-Tigo-SuperApp-AirTimeTopup` · **Type:** service · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `7a52359`
**Purpose:** Airtime and fiber product top-up

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** MassTransit.RabbitMQ, Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-AIRTIME-001 | `POST /api/FiberProduct/GetReferenceNumberValidation` | `FiberProductController.GetReferenceNumberValidation` | FiberProductController.GetReferenceNumberValidation | see contract | confirmed |
| BE-API-AIRTIME-002 | `POST /api/FiberProduct/SubmitPayment` | `FiberProductController.SubmitPayment` | FiberProductController.SubmitPayment | see contract | confirmed |
| BE-API-AIRTIME-003 | `POST /api/FiberProduct/SubmitPaymentCapacityChange` | `FiberProductController.SubmitPaymentCapacityChange` | FiberProductController.SubmitPaymentCapacityChange | see contract | confirmed |
| BE-API-AIRTIME-004 | `POST /api/FiberProduct/GetReferenceNumberValidationForCapacityChange` | `FiberProductController.GetReferenceNumberCapacityChange` | FiberProductController.GetReferenceNumberCapacityChange | see contract | confirmed |
| BE-API-AIRTIME-005 | `POST /api/AirTime/AirTimeTopUp` | `AirTimeController.AirTimeTopUp` | AirTimeController.AirTimeTopUp | see contract | confirmed |
| BE-API-AIRTIME-006 | `POST /api/AirTime/AirTimeTopUpV1` | `AirTimeController.AirTimeTopUpV1` | AirTimeController.AirTimeTopUpV1 | see contract | confirmed |
| BE-API-AIRTIME-007 | `POST /api/AirTime/VerifySendMoney` | `AirTimeController.VerifySendMoney` | AirTimeController.VerifySendMoney | see contract | confirmed |
| BE-API-AIRTIME-008 | `POST /api/AirTime/AirTimeTopUpOthers` | `AirTimeController.AirTimeTopUpOthers` | AirTimeController.AirTimeTopUpOthers | see contract | confirmed |
| BE-API-AIRTIME-009 | `POST /api/AirTime/enc` | `AirTimeController.enc` | AirTimeController.enc | see contract | confirmed |
| BE-API-AIRTIME-010 | `POST /api/AirTime/dec` | `AirTimeController.dec` | AirTimeController.dec | see contract | partial |

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
| `BaseEntity` / `—` | `TZTigoSuperAppAirTimeTopup/Data/Entities/BaseEntity.cs` |
| `Token` / `—` | `TZTigoSuperAppAirTimeTopup/Domain/Model/Token.cs` |
| `ResponseCodeResponse` / `—` | `TZTigoSuperAppAirTimeTopup/Domain/Model/ResponseCodeResponse.cs` |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`AirTimeTopUp`, `ConfigAPIUrl`, `EnableLog`, `Encryption_Decryption_Key`, `FCMNotify`, `FiberProduct:<redacted-purpose>`, `FiberProduct:CapacityChangeShortCode`, `FiberProduct:MonthlyPlanShortCode`, `FiberProduct:ReferenceValidationURL`, `FiberProduct:SessionID`, `FiberProduct:SubmitPaymentTerminalType`, `FiberProduct:SubmitPaymentURL`, `FiberProduct:TerminalType`, `FiberProduct:UserName`, `IV`, `MTPGPaymentRequest:ConsumerID`, `MTPGPaymentRequest:PaymentType`, `MTPGPaymentRequest:TerminalType`, `MTPGPaymentRequest:URL`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:IsHttpsRabbitMQ`, `RabbitMQ:LogQueueName`, `RabbitMQ:LogURL`, `RabbitMQ:Port`, `RabbitMQ:QueueName`, `RabbitMQ:URL`, `RabbitMQ:Username`, `RedisURL`, `SaveLogs`, `SendAuditLogsViaService`, `SendFCMViaService`, `Tanzania`, `Tanzania:responseChanel`, `Tanzania:serviceName`, `TanzaniaAPI`, `TokenKey`, `VerifySendMoney:ConsumerID`, `VerifySendMoney:OperatorsInformation`, `VerifySendMoney:TANQR`, `VerifySendMoney:TerminalType`

## Open questions
- Gateway public URLs not in-repo.
