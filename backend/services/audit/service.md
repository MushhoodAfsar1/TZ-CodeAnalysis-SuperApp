---
kb_section: backend
type: service
ids: [BE-SVC-AUDIT]
service: AUDIT
repo: TZ-Tigo-SuperApp-AuditLogs
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: eb87819
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-AUDIT Audit log ingestion / query
**Repo:** `TZ-Tigo-SuperApp-AuditLogs` · **Type:** service · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `eb87819`
**Purpose:** Audit log ingestion / query

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** MassTransit, MassTransit.RabbitMQ, Microsoft.AspNetCore.Authentication.JwtBearer, Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-AUDIT-001 | `POST /api/Logs/create` | `LogsController.CreateLogsAsync` | LogsController.CreateLogsAsync | see contract | confirmed |

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
| `BaseResponse` / `—` | `TZTigoSuperAppAuditLogs/Domain/App/BaseResponse.cs` |
| `CloudStorage` / `—` | `TZTigoSuperAppAuditLogs/Domain/Implementation/CloudStorage.cs` |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `EnableLog:Warning`, `Encryption_Decryption_Key`, `IV`, `Origins`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:LogQueueName`, `RabbitMQ:LogURL`, `RabbitMQ:Username`, `isEncrypted`

## Open questions
- Gateway public URLs not in-repo.
