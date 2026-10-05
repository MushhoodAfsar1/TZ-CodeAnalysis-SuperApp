---
kb_section: backend
type: service
ids: [BE-SVC-VCARD]
service: VCARD
repo: TZ-Tigo-SuperApp-VirtualCard
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: db358e6
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-VCARD Virtual card issuance
**Repo:** `TZ-Tigo-SuperApp-VirtualCard` · **Type:** service · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `db358e6`
**Purpose:** Virtual card issuance

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, RabbitMQ.Client, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-VCARD-001 | `POST /api/CardManagement/GetCardList` | `CardManagementController.GetCardList` | CardManagementController.GetCardList | see contract | confirmed |
| BE-API-VCARD-002 | `POST /api/CardManagement/GetCardValidity` | `CardManagementController.GetCardValidity` | CardManagementController.GetCardValidity | see contract | confirmed |
| BE-API-VCARD-003 | `POST /api/CardManagement/CreateMasterCard` | `CardManagementController.CreateMasterCard` | CardManagementController.CreateMasterCard | see contract | confirmed |
| BE-API-VCARD-004 | `POST /api/CardManagement/GetCardTransaction` | `CardManagementController.GetCardTransaction` | CardManagementController.GetCardTransaction | see contract | confirmed |
| BE-API-VCARD-005 | `POST /api/CardManagement/GetCardDetail` | `CardManagementController.GetCardDetail` | CardManagementController.GetCardDetail | see contract | confirmed |
| BE-API-VCARD-006 | `POST /api/CardManagement/EnableDisableCard` | `CardManagementController.EnableDisableCard` | CardManagementController.EnableDisableCard | see contract | confirmed |
| BE-API-VCARD-007 | `POST /api/CardManagement/DeleteCard` | `CardManagementController.DeleteCard` | CardManagementController.DeleteCard | see contract | confirmed |
| BE-API-VCARD-008 | `POST /api/CardManagement/GetValidityDays` | `CardManagementController.GetValidityDays` | CardManagementController.GetValidityDays | see contract | confirmed |
| BE-API-VCARD-009 | `POST /api/CardManagement/enc` | `CardManagementController.enc` | CardManagementController.enc | see contract | confirmed |

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
| `BaseEntity` / `—` | `TZTigoSuperAppVirtualCard/Data/Entities/BaseEntity.cs` |
| `VirtualCardManagementRepository` / `—` | `TZTigoSuperAppVirtualCard/Domain/Repositories/VirtualCardManagementRepository.cs` |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`ConfigAPIUrl`, `CreateCard`, `DeleteCard`, `EnableDisableCard`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `EnableLog:Warning`, `Encryption_Decryption_Key`, `FCMNotify`, `GetValidityDays`, `IV`, `IsRedisCluster`, `ListOfCards`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:LogQueueName`, `RabbitMQ:LogURL`, `RabbitMQ:QueueName`, `RabbitMQ:Username`, `RedisPassword (key name)<redacted-purpose>`, `RedisURL`, `SaveLogs`, `SendAuditLogsViaService`, `SendFCMViaService`, `Tanzania:responseChanel`, `TanzaniaAPI:<redacted-purpose>`, `TanzaniaAPI:Username`, `TokenKey`, `VCNToken`, `ViewCardDetails`, `ViewTransactions`, `is_encrypted`, `responseChanel`, `serviceName`

## Open questions
- Gateway public URLs not in-repo.
