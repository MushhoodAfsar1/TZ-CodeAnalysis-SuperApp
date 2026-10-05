---
kb_section: backend
type: service
ids: [BE-SVC-SESS]
service: SESS
repo: TZ-Tigo-SuperApp-Session
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 6f24061
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-SESS Mobile session JWT issuance
**Repo:** `TZ-Tigo-SuperApp-Session` · **Type:** auth/identity · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `6f24061`
**Purpose:** Mobile session JWT issuance

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** MassTransit.RabbitMQ, Microsoft.AspNetCore.Authentication.JwtBearer, Microsoft.AspNetCore.Identity.EntityFrameworkCore, Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Design, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, Serilog, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, Serilog.Sinks.Console, StackExchange.Redis, Swashbuckle.AspNetCore.SwaggerGen, Swashbuckle.AspNetCore.SwaggerUI

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-SESS-001 | `POST /api/Account/auth` | `AccountController.Auth` | AccountController.Auth | see contract | confirmed |
| BE-API-SESS-002 | `POST /api/Account/refreshToken` | `AccountController.Refresh` | AccountController.Refresh | see contract | confirmed |
| BE-API-SESS-003 | `POST /api/Account/enc` | `AccountController.enc_payment` | AccountController.enc_payment | see contract | confirmed |
| BE-API-SESS-004 | `POST /api/Account/decreq` | `AccountController.dec_req` | AccountController.dec_req | see contract | partial |

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
| `AppplicationContext` / `—` | `TZTigoSuperAppSession/Domain/AppplicationContext.cs` |
| `ConnectionStringOptions` / `—` | `TZTigoSuperAppSession/Domain/AppplicationContext.cs` |
| `DataContext` / `—` | `TZTigoSuperAppSession/Domain/DBContext/DataContext.cs` |
| `RepositoryContext` / `—` | `TZTigoSuperAppSession/Domain/DBContext/RepositoryContext.cs` |
| `TokenRepository` / `—` | `TZTigoSuperAppSession/Domain/Repositories/TokenRepository.cs` |
| `ProfileRepository` / `—` | `TZTigoSuperAppSession/Domain/Repositories/ProfileRepository.cs` |
| `RepositoryManager` / `—` | `TZTigoSuperAppSession/Domain/Repositories/RepositoryManager.cs` |
| `RepositoryBase` / `—` | `TZTigoSuperAppSession/Domain/Repositories/RepositoryBase.cs` |
| `BaseResponse` / `—` | `TZTigoSuperAppSession/Domain/Models/BaseResponse.cs` |
| `BaseResponseChannel` / `—` | `TZTigoSuperAppSession/Domain/Models/BaseResponse.cs` |
| `TokenResponse` / `—` | `TZTigoSuperAppSession/Domain/Models/BaseResponse.cs` |
| `BaseModel` / `—` | `TZTigoSuperAppSession/Domain/Models/BaseModel.cs` |
| `AuditLogsRequest` / `—` | `TZTigoSuperAppSession/Domain/Models/GenericModel/AuditLogsRequest.cs` |
| `Tokens` / `—` | `TZTigoSuperAppSession/Domain/Models/Entities/token.cs` |
| `Device` / `—` | `TZTigoSuperAppSession/Domain/Models/Entities/device.cs` |
| `RefreshTokenDto` / `—` | `TZTigoSuperAppSession/Domain/Models/Entities/RefreshTokenDto.cs` |
| `Profile` / `—` | `TZTigoSuperAppSession/Domain/Models/Entities/profile.cs` |
| `ResponseCodeRequest` / `—` | `TZTigoSuperAppSession/Domain/Models/ResponseCode/ResponseCodeRequest.cs` |
| `ResponseCodeResponse` / `—` | `TZTigoSuperAppSession/Domain/Models/ResponseCode/ResponseCodeResponse.cs` |
| `TokenDto` / `—` | `TZTigoSuperAppSession/Domain/Models/SessionManagementModel/TokenDto.cs` |
| `EncryptedRequest` / `—` | `TZTigoSuperAppSession/Domain/Models/GenericModel/Request/EncryptedRequest.cs` |
| `BaseRequest` / `—` | `TZTigoSuperAppSession/Domain/Models/GenericModel/Request/BaseRequest.cs` |
| `BaseResponse` / `—` | `TZTigoSuperAppSession/Domain/Models/GenericModel/Response/BaseResponse.cs` |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`ConnectionStrings:<redacted-purpose>`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `EnableLog:Warning`, `Encryption_Decryption_Key`, `IV`, `IsRedisCluster`, `JwtExpiryMins`, `JwtRefreshExpiryMins`, `Origins`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:IsHttpsRabbitMQ`, `RabbitMQ:LogQueueName`, `RabbitMQ:LogURL`, `RabbitMQ:Port`, `RabbitMQ:Username`, `RedisPassword (key name)<redacted-purpose>`, `RedisURL`, `SaveLogs`, `SendAuditLogsViaService`, `TokenKey`, `is_encrypted`

## Open questions
- Gateway public URLs not in-repo.
