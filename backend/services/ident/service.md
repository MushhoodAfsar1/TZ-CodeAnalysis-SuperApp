---
kb_section: backend
type: service
ids: [BE-SVC-IDENT]
service: IDENT
repo: TZ-Tigo-SuperApp-Identity
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: e7397b0
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-IDENT Identity / admin IAM
**Repo:** `TZ-Tigo-SuperApp-Identity` · **Type:** auth/identity · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `e7397b0`
**Purpose:** Identity / admin IAM

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** MassTransit.RabbitMQ, Microsoft.AspNetCore.Authentication.JwtBearer, Microsoft.AspNetCore.Identity.EntityFrameworkCore, Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.InMemory, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore.SwaggerGen, Swashbuckle.AspNetCore.SwaggerUI

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-IDENT-001 | `POST /api/Permission/getall` | `PermissionController.getAll` | PermissionController.getAll | see contract | confirmed |
| BE-API-IDENT-002 | `POST /api/Permission/add` | `PermissionController.add` | PermissionController.add | see contract | confirmed |
| BE-API-IDENT-003 | `POST /api/Permission/update` | `PermissionController.update` | PermissionController.update | see contract | confirmed |
| BE-API-IDENT-004 | `POST /api/Permission/get` | `PermissionController.get` | PermissionController.get | see contract | confirmed |
| BE-API-IDENT-005 | `POST /api/Permission/delete` | `PermissionController.delete` | PermissionController.delete | see contract | confirmed |
| BE-API-IDENT-006 | `POST /api/Permission/getrolebasedall` | `PermissionController.getrolebasedall` | PermissionController.getrolebasedall | see contract | confirmed |
| BE-API-IDENT-007 | `POST /api/Menu/getall` | `MenuController.getAll` | MenuController.getAll | see contract | confirmed |
| BE-API-IDENT-008 | `POST /api/Menu/add` | `MenuController.add` | MenuController.add | see contract | confirmed |
| BE-API-IDENT-009 | `POST /api/Menu/update` | `MenuController.update` | MenuController.update | see contract | confirmed |
| BE-API-IDENT-010 | `POST /api/Menu/get` | `MenuController.get` | MenuController.get | see contract | confirmed |
| BE-API-IDENT-011 | `POST /api/Menu/getsubmenuall` | `MenuController.getsubmenuall` | MenuController.getsubmenuall | see contract | confirmed |
| BE-API-IDENT-012 | `POST /api/Menu/delete` | `MenuController.delete` | MenuController.delete | see contract | confirmed |
| BE-API-IDENT-013 | `GET /Welcome/Index` | `WelcomeController.Index` | WelcomeController.Index | see contract | partial |
| BE-API-IDENT-014 | `POST /api/Account/register` | `AccountController.register` | AccountController.register | see contract | confirmed |
| BE-API-IDENT-015 | `POST /api/Account/update` | `AccountController.update` | AccountController.update | see contract | confirmed |
| BE-API-IDENT-016 | `POST /api/Account/delete` | `AccountController.delete` | AccountController.delete | see contract | confirmed |
| BE-API-IDENT-017 | `POST /api/Account/login` | `AccountController.Login` | AccountController.Login | see contract | confirmed |
| BE-API-IDENT-018 | `POST /api/Account/loginwithad` | `AccountController.LoginWithAD` | AccountController.LoginWithAD | see contract | confirmed |
| BE-API-IDENT-019 | `GET /api/Account/getaduserdetail` | `AccountController.GetADUserDetail` | AccountController.GetADUserDetail | see contract | confirmed |
| BE-API-IDENT-020 | `POST /api/Account/login2fa` | `AccountController.LoginWithOTP` | AccountController.LoginWithOTP | see contract | confirmed |
| BE-API-IDENT-021 | `POST /api/Account/resendotp` | `AccountController.ResendOtp` | AccountController.ResendOtp | see contract | confirmed |
| BE-API-IDENT-022 | `POST /api/Account/getusers` | `AccountController.GetUsers` | AccountController.GetUsers | see contract | confirmed |
| BE-API-IDENT-023 | `POST /api/Account/logout` | `AccountController.LogOut` | AccountController.LogOut | see contract | confirmed |
| BE-API-IDENT-024 | `POST /api/Account/passwordchangeuser` | `AccountController.passwordchangeuser` | AccountController.passwordchangeuser | see contract | confirmed |
| BE-API-IDENT-025 | `POST /api/Account/passwordchange` | `AccountController.passwordchange` | AccountController.passwordchange | see contract | confirmed |
| BE-API-IDENT-026 | `POST /api/Account/getroles` | `AccountController.getroles` | AccountController.getroles | see contract | confirmed |
| BE-API-IDENT-027 | `POST /api/Account/addrole` | `AccountController.addrole` | AccountController.addrole | see contract | confirmed |
| BE-API-IDENT-028 | `POST /api/Account/updaterole` | `AccountController.updaterole` | AccountController.updaterole | see contract | confirmed |
| BE-API-IDENT-029 | `POST /api/Account/userroles` | `AccountController.userroles` | AccountController.userroles | see contract | confirmed |
| BE-API-IDENT-030 | `POST /api/Account/adduserrole` | `AccountController.adduserrole` | AccountController.adduserrole | see contract | confirmed |
| BE-API-IDENT-031 | `POST /api/Account/removeuserrole` | `AccountController.removeuserrole` | AccountController.removeuserrole | see contract | confirmed |
| BE-API-IDENT-032 | `POST /api/Account/addroleclaim` | `AccountController.addroleclaim` | AccountController.addroleclaim | see contract | confirmed |
| BE-API-IDENT-033 | `POST /api/Account/removeroleclaim` | `AccountController.removeroleclaim` | AccountController.removeroleclaim | see contract | confirmed |
| BE-API-IDENT-034 | `POST /api/Account/getAuditLogs` | `AccountController.getAuditLogs` | AccountController.getAuditLogs | see contract | confirmed |

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
| `ApplicationUser` / `User` | EF set |
| `Application` / `Application` | EF set |
| `UserApplication` / `UserApplication` | EF set |
| `Menu` / `Menu` | EF set |
| `Permission` / `Permission` | EF set |
| `Audit` / `AuditLogs` | EF set |
| `TwoFactorAuthentication` / `TwoFactorAuthentications` | EF set |
| `T` / `dbSet` | EF set |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`DefaultOtp`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `EnableLog:Warning`, `Encryption_Decryption_Key`, `IV`, `IsRedisCluster`, `JwtExpiryMins`, `LDAP:<redacted-purpose>`, `LDAP:BaseDN`, `LDAP:Domain`, `LDAP:Port`, `LDAP:Servers`, `LDAP:Username`, `Origins`, `OtpExpirySeconds`, `OtpLength`, `OtpSMSKeyforAutoFetch`, `RabbitMQ:LogQueueName`, `RedisPassword (key name)<redacted-purpose>`, `RedisURL`, `ResetPasswordDays:<redacted-purpose>`, `ResetPasswordNotificationDays:<redacted-purpose>`, `SaveLogs`, `SendAuditLogsViaService`, `SendEMail`, `Tanzania:<redacted-purpose>`, `Tanzania:SendSMS:Username`, `Tanzania:SendSMS:consumerID`, `Tanzania:SendSMS:smsShortCode`, `TokenKey`, `is_encrypted`

## Open questions
- Gateway public URLs not in-repo.
