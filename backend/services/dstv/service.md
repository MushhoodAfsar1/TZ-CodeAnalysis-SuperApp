---
kb_section: backend
type: service
ids: [BE-SVC-DSTV]
service: DSTV
repo: TZ-Tigo-SuperApp-DigitalSubscription
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: fd31aa1
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-DSTV Digital / DSTV subscriptions
**Repo:** `TZ-Tigo-SuperApp-DigitalSubscription` · **Type:** service · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `fd31aa1`
**Purpose:** Digital / DSTV subscriptions

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** MassTransit.RabbitMQ, Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-DSTV-001 | `POST /api/DSTV/GetCustomerDetail` | `DSTVController.GetCustomerDetail` | DSTVController.GetCustomerDetail | see contract | confirmed |
| BE-API-DSTV-002 | `POST /api/DSTV/GetDueAmount` | `DSTVController.GetDueAmount` | DSTVController.GetDueAmount | see contract | confirmed |
| BE-API-DSTV-003 | `POST /api/DSTV/GetAvailableProducts` | `DSTVController.GetAvailableProducts` | DSTVController.GetAvailableProducts | see contract | confirmed |
| BE-API-DSTV-004 | `POST /api/DSTV/SubmitPaymentBySmartcard` | `DSTVController.SubmitPaymentBySmartcard` | DSTVController.SubmitPaymentBySmartcard | see contract | confirmed |
| BE-API-DSTV-005 | `POST /api/DSTV/PaymentConfirmation` | `DSTVController.PaymentConfirmation` | DSTVController.PaymentConfirmation | see contract | confirmed |
| BE-API-DSTV-006 | `POST /api/DSTV/CustomerDetailenc` | `DSTVController.CustomerDetailenc` | DSTVController.CustomerDetailenc | see contract | confirmed |
| BE-API-DSTV-007 | `POST /api/DSTV/DueAmountenc` | `DSTVController.DueAmountenc` | DSTVController.DueAmountenc | see contract | confirmed |

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
| `Token` / `—` | `TZTigoSuperAppDigitalSubscription/Domain/Model/Token.cs` |
| `DSTVPackagesRepository` / `—` | `TZTigoSuperAppDigitalSubscription/Domain/Repositories/DSTVPackagesRepository.cs` |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`BusinessUnit`, `ConfigAPIUrl`, `CustomerNumber`, `Datasource`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `EnableLog:Warning`, `Encryption_Decryption_Key`, `IV`, `IsRedisCluster`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:LogQueueName`, `RabbitMQ:LogURL`, `RabbitMQ:Username`, `RedisPassword (key name)<redacted-purpose>`, `RedisURL`, `SaveLogs`, `SendAuditLogsViaService`, `Tigo2DSTVGetAvailableProducts`, `Tigo2DSTVGetCustomerDetailsByDeviceNumber`, `Tigo2DSTVGetDueAmountandDate`, `Tigo2DSTVPaymentConfirmation`, `Tigo2DSTVSubmitPaymentBySmartcard`, `TokenKey`, `VendorCode`, `apiResponseChanel`, `is_encrypted`, `serviceName`

## Open questions
- Gateway public URLs not in-repo.
