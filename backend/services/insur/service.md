---
kb_section: backend
type: service
ids: [BE-SVC-INSUR]
service: INSUR
repo: TZ-Tigo-SuperApp-Insurrance
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 38747da
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-INSUR Insurance purchase
**Repo:** `TZ-Tigo-SuperApp-Insurrance` · **Type:** service · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `38747da`
**Purpose:** Insurance purchase

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** MassTransit.RabbitMQ, Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, RabbitMQ.Client, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-INSUR-001 | `POST /api/Insurance/GetVehicleDetails` | `InsuranceController.GetVehicleDetails` | InsuranceController.GetVehicleDetails | see contract | confirmed |
| BE-API-INSUR-002 | `POST /api/Insurance/GetMotorVehicleDetails` | `InsuranceController.GetMotorVehicleDetails` | InsuranceController.GetMotorVehicleDetails | see contract | confirmed |
| BE-API-INSUR-003 | `POST /api/Insurance/ConfirmVehicleRegistration` | `InsuranceController.ConfirmVehicleRegistration` | InsuranceController.ConfirmVehicleRegistration | see contract | confirmed |
| BE-API-INSUR-004 | `POST /api/Insurance/GetQuote` | `InsuranceController.GetQuote` | InsuranceController.GetQuote | see contract | confirmed |
| BE-API-INSUR-005 | `POST /api/Insurance/GetQuoteV1` | `InsuranceController.GetQuoteV1` | InsuranceController.GetQuoteV1 | see contract | confirmed |
| BE-API-INSUR-006 | `POST /api/Insurance/MTPGBillQuery` | `InsuranceController.MTPGBillQuery` | InsuranceController.MTPGBillQuery | see contract | confirmed |
| BE-API-INSUR-007 | `POST /api/Insurance/PaymentNotification` | `InsuranceController.PaymentNotification` | InsuranceController.PaymentNotification | see contract | confirmed |
| BE-API-INSUR-008 | `POST /api/Conversion/encGetVehicleDetails` | `ConversionController.encGetVehicleDetails` | ConversionController.encGetVehicleDetails | see contract | confirmed |
| BE-API-INSUR-009 | `POST /api/Conversion/encGetMotorVehicleDetails` | `ConversionController.encGetMotorVehicleDetails` | ConversionController.encGetMotorVehicleDetails | see contract | confirmed |
| BE-API-INSUR-010 | `POST /api/Conversion/encConfirmVehicleRegistration` | `ConversionController.encConfirmVehicleRegistration` | ConversionController.encConfirmVehicleRegistration | see contract | confirmed |
| BE-API-INSUR-011 | `POST /api/Conversion/encGetQuote` | `ConversionController.encGetQuote` | ConversionController.encGetQuote | see contract | confirmed |
| BE-API-INSUR-012 | `POST /api/Conversion/encMTPGBillQuery` | `ConversionController.encMTPGBillQuery` | ConversionController.encMTPGBillQuery | see contract | confirmed |
| BE-API-INSUR-013 | `POST /api/Conversion/encPaymentNotification` | `ConversionController.encPaymentNotification` | ConversionController.encPaymentNotification | see contract | confirmed |

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
| `BaseEntity` / `—` | `TZTigoSuperAppInsurance/Data/Entities/BaseEntity.cs` |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`ConfigAPIUrl`, `ConfirmVehicleRegistrationURL`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `Encryption_Decryption_Key`, `GetMotorVehicleDetailsURL`, `GetQuoteURL`, `IV`, `IsRedisCluster`, `MTPGBillQueryURL`, `PaymentNotificationURL`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:IsHttpsRabbitMQ`, `RabbitMQ:LogQueueName`, `RabbitMQ:Port`, `RabbitMQ:URL`, `RabbitMQ:Username`, `RedisPassword (key name)<redacted-purpose>`, `RedisURL`, `SaveLogs`, `SendAuditLogsViaService`, `Tanzania:ConsumerId`, `Tanzania:responseChanel`, `Tanzania:serviceName`, `TokenKey`, `VehicalDetailURL`, `goods`, `is_encrypted`, `passengers`, `personal`, `responseChanel`

## Open questions
- Gateway public URLs not in-repo.
