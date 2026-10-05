---
kb_section: backend
type: service
ids: [BE-SVC-EXPENSE]
service: EXPENSE
repo: TZ-Tigo-SuperApp-Expense
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: e821ac9
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-EXPENSE Expense and advance salary
**Repo:** `TZ-Tigo-SuperApp-Expense` · **Type:** service · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `e821ac9`
**Purpose:** Expense and advance salary

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** MassTransit.RabbitMQ, Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-EXPENSE-001 | `POST /api/AdvanceSalary/GetHolidayList` | `AdvanceSalaryController.GetHolidayList` | AdvanceSalaryController.GetHolidayList | see contract | confirmed |
| BE-API-EXPENSE-002 | `POST /api/AdvanceSalary/GetCompanyConfig` | `AdvanceSalaryController.GetCompanyConfig` | AdvanceSalaryController.GetCompanyConfig | see contract | confirmed |
| BE-API-EXPENSE-003 | `POST /api/AdvanceSalary/SalaryAdvanceRequest` | `AdvanceSalaryController.SalaryAdvanceRequest` | AdvanceSalaryController.SalaryAdvanceRequest | see contract | confirmed |
| BE-API-EXPENSE-004 | `POST /api/AdvanceSalary/SalaryAdvanceStop` | `AdvanceSalaryController.SalaryAdvanceStop` | AdvanceSalaryController.SalaryAdvanceStop | see contract | confirmed |
| BE-API-EXPENSE-005 | `POST /api/AdvanceSalary/GetSalaryAdvanceRequests` | `AdvanceSalaryController.GetSalaryAdvanceRequests` | AdvanceSalaryController.GetSalaryAdvanceRequests | see contract | confirmed |
| BE-API-EXPENSE-006 | `POST /api/AdvanceSalary/EditSalaryAdvanceRequest` | `AdvanceSalaryController.EditSalaryAdvanceRequest` | AdvanceSalaryController.EditSalaryAdvanceRequest | see contract | confirmed |
| BE-API-EXPENSE-007 | `POST /api/ExpenseManagement/CheckWhitelisted` | `ExpenseManagementController.CheckWhitelisted` | ExpenseManagementController.CheckWhitelisted | see contract | confirmed |
| BE-API-EXPENSE-008 | `POST /api/ExpenseManagement/GetInitiatorList` | `ExpenseManagementController.GetInitiatorList` | ExpenseManagementController.GetInitiatorList | see contract | confirmed |
| BE-API-EXPENSE-009 | `POST /api/ExpenseManagement/BankDetail` | `ExpenseManagementController.BankDetail` | ExpenseManagementController.BankDetail | see contract | confirmed |
| BE-API-EXPENSE-010 | `POST /api/ExpenseManagement/GetExpense` | `ExpenseManagementController.GetExpense` | ExpenseManagementController.GetExpense | see contract | confirmed |
| BE-API-EXPENSE-011 | `POST /api/ExpenseManagement/CreateExpense` | `ExpenseManagementController.CreateExpense` | ExpenseManagementController.CreateExpense | see contract | confirmed |
| BE-API-EXPENSE-012 | `POST /api/ExpenseManagement/CreateRetirement` | `ExpenseManagementController.CreateRetirement` | ExpenseManagementController.CreateRetirement | see contract | confirmed |
| BE-API-EXPENSE-013 | `POST /api/ExpenseManagement/GetOtherInitiator` | `ExpenseManagementController.GetOtherInitiator` | ExpenseManagementController.GetOtherInitiator | see contract | confirmed |
| BE-API-EXPENSE-014 | `POST /api/ExpenseManagement/ChangeInitiator` | `ExpenseManagementController.ChangeInitiator` | ExpenseManagementController.ChangeInitiator | see contract | confirmed |
| BE-API-EXPENSE-015 | `POST /api/ExpenseManagement/enc` | `ExpenseManagementController.enc` | ExpenseManagementController.enc | see contract | confirmed |

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
| `expense` / `expenses` | EF set |
| `retirement` / `retirements` | EF set |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`BusinessPortalAPIURL`, `BusinessPortalAPIURL:UseNewAPI`, `ConfigAPIUrl`, `ConfigurationManagementApi:GetAllAppConfigPath`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `EnableLog:Warning`, `Encryption_Decryption_Key`, `IV`, `IsRedisCluster`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:IsHttpsRabbitMQ`, `RabbitMQ:LogQueueName`, `RabbitMQ:LogURL`, `RabbitMQ:Port`, `RabbitMQ:Username`, `RedisPassword (key name)<redacted-purpose>`, `RedisURL`, `SaveLogs`, `SendAuditLogsViaService`, `Tanzania:responseChanel`, `TanzaniaAPI`, `TanzaniaAPI:<redacted-purpose>`, `TanzaniaAPI:Username`, `TokenKey`, `UseCustomCipherSuites`, `is_encrypted`, `responseChanel`, `serviceName`

## Open questions
- Gateway public URLs not in-repo.
