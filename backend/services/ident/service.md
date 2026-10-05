---
kb_section: backend
type: service
ids: [BE-SVC-IDENT]
service: IDENT
repo: TZ-Tigo-SuperApp-Identity
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: e7397b0
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-IDENT TZ-Tigo-SuperApp-Identity
**Repo:** `TZ-Tigo-SuperApp-Identity` · **Type:** auth/identity · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `e7397b0`
**Purpose:** Identity / KYC / portal login (ASP.NET Identity + LDAP)

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-IDENT-001 | POST /api/Permission/getall | PermissionController.getAll | — | JWT | confirmed |
| BE-API-IDENT-002 | POST /api/Permission/add | PermissionController.add | — | JWT | confirmed |
| BE-API-IDENT-003 | POST /api/Permission/update | PermissionController.update | — | JWT | confirmed |
| BE-API-IDENT-004 | POST /api/Permission/get | PermissionController.get | — | JWT | confirmed |
| BE-API-IDENT-005 | POST /api/Permission/delete | PermissionController.delete | — | JWT | confirmed |
| BE-API-IDENT-006 | POST /api/Permission/getrolebasedall | PermissionController.getrolebasedall | — | JWT | confirmed |
| BE-API-IDENT-007 | POST /api/Menu/getall | MenuController.getAll | — | JWT | confirmed |
| BE-API-IDENT-008 | POST /api/Menu/add | MenuController.add | — | JWT | confirmed |
| BE-API-IDENT-009 | POST /api/Menu/update | MenuController.update | — | JWT | confirmed |
| BE-API-IDENT-010 | POST /api/Menu/get | MenuController.get | — | JWT | confirmed |
| BE-API-IDENT-011 | POST /api/Menu/getsubmenuall | MenuController.getsubmenuall | — | JWT | confirmed |
| BE-API-IDENT-012 | POST /api/Menu/delete | MenuController.delete | — | JWT | confirmed |
| BE-API-IDENT-013 | POST /api/Account/register | AccountController.register | — | JWT | confirmed |
| BE-API-IDENT-014 | POST /api/Account/update | AccountController.update | — | JWT | confirmed |
| BE-API-IDENT-015 | POST /api/Account/delete | AccountController.delete | — | JWT | confirmed |
| BE-API-IDENT-016 | POST /api/Account/login | AccountController.Login | — | JWT | confirmed |
| BE-API-IDENT-017 | POST /api/Account/loginwithad | AccountController.LoginWithAD | — | JWT | confirmed |
| BE-API-IDENT-018 | GET /api/Account/getaduserdetail | AccountController.GetADUserDetail | — | JWT | confirmed |
| BE-API-IDENT-019 | POST /api/Account/login2fa | AccountController.LoginWithOTP | — | JWT | confirmed |
| BE-API-IDENT-020 | POST /api/Account/resendotp | AccountController.ResendOtp | — | JWT | confirmed |
| BE-API-IDENT-021 | POST /api/Account/getusers | AccountController.GetUsers | — | JWT | confirmed |
| BE-API-IDENT-022 | POST /api/Account/logout | AccountController.LogOut | — | JWT | confirmed |
| BE-API-IDENT-023 | POST /api/Account/passwordchangeuser | AccountController.passwordchangeuser | — | anon | confirmed |
| BE-API-IDENT-024 | POST /api/Account/passwordchange | AccountController.passwordchange | — | JWT | confirmed |
| BE-API-IDENT-025 | POST /api/Account/getroles | AccountController.getroles | — | JWT | confirmed |
| BE-API-IDENT-026 | POST /api/Account/addrole | AccountController.addrole | — | JWT | confirmed |
| BE-API-IDENT-027 | POST /api/Account/updaterole | AccountController.updaterole | — | JWT | confirmed |
| BE-API-IDENT-028 | POST /api/Account/userroles | AccountController.userroles | — | JWT | confirmed |
| BE-API-IDENT-029 | POST /api/Account/adduserrole | AccountController.adduserrole | — | JWT | confirmed |
| BE-API-IDENT-030 | POST /api/Account/removeuserrole | AccountController.removeuserrole | — | JWT | confirmed |
| BE-API-IDENT-031 | POST /api/Account/addroleclaim | AccountController.addroleclaim | — | JWT | confirmed |
| BE-API-IDENT-032 | POST /api/Account/removeroleclaim | AccountController.removeroleclaim | — | JWT | confirmed |
| BE-API-IDENT-033 | POST /api/Account/getAuditLogs | AccountController.getAuditLogs | — | JWT | confirmed |
| BE-API-IDENT-034 | GET /Welcome/Index | WelcomeController.Index | — | none | confirmed |


## Dependencies
| Calls | Sync/Async | Why |
|---|---|---|
| Session / Account / Config (typical) | Sync HTTP | Token and profile checks |
| Called by | Sync/Async | Why |
| Mobile app / portal | Sync | User journeys |

## Data owned
| Entity / table | Purpose |
|---|---|
| See data-model.md | — |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`TokenKey`, `isEncrypted`/`is_encrypted`, `Encryption_Decryption_Key`, `IV`, `JwtExpiryMins`, `PostgresConnection` (name only)

## Open questions
Status this run: **deep-analyzed**
