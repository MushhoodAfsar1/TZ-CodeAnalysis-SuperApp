---
kb_section: backend
type: service
ids: [BE-SVC-MCHRPT]
service: MCHRPT
repo: TZ-Tigo-SuperApp-MChangoReportScheduler
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 34ba77f
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-MCHRPT MChango reports and interest
**Repo:** `TZ-Tigo-SuperApp-MChangoReportScheduler` · **Type:** batch/scheduler · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `34ba77f`
**Purpose:** MChango reports and interest

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** FluentValidation, FluentValidation.AspNetCore, Microsoft.AspNetCore.Authentication.JwtBearer, Microsoft.AspNetCore.Identity.EntityFrameworkCore, Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, RabbitMQ.Client, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

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
| `T` / `_entities` | EF set |
| `T` / `Entities` | EF set |
| `T` / `Table` | EF set |
| `T` / `Table` | EF set |
| `mchangointerestconfiguration` / `mchangointerestconfiguration` | EF set |
| `AccountEntityModel` / `Accounts` | EF set |
| `PledgeTransactionEntityModel` / `PledgeTransactions` | EF set |
| `InvitationEntityModel` / `Invitations` | EF set |
| `AccountDurationTypeEntityModel` / `AccountDurationTypes` | EF set |
| `TransactionHistoryEntityModel` / `TransactionHistory` | EF set |
| `MChangoReportRequestsEntityModel` / `MChangoReportRequests` | EF set |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`ConfigAPIUrl`, `EmailCC`, `EmailTo`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `EnableLog:Warning`, `Encryption_Decryption_Key`, `GetBalance`, `IV`, `IsRedisCluster`, `MChangoImage`, `MIXXBanner`, `MIXXLogo`, `MaxRecords`, `Partner:ApiBaseUrl`, `Partner:XAuthKey`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:IsHttpsRabbitMQ`, `RabbitMQ:Port`, `RabbitMQ:URL`, `RabbitMQ:Username`, `RedisPassword (key name)<redacted-purpose>`, `RedisURL`, `ServiceDelayTimeMin`, `SmtpPassword (key name)<redacted-purpose>`, `SmtpPort`, `SmtpServer`, `SmtpUsername`, `Tanzania:<redacted-purpose>`, `Tanzania:ChannelUser`, `Tanzania:SendMoneyFeeCheck:ConsumerID:APP`, `responseChanel`, `serviceName`

## Open questions
- Gateway public URLs not in-repo.
