---
kb_section: backend
type: service
ids: [BE-SVC-EXPENSE]
service: EXPENSE
repo: TZ-Tigo-SuperApp-Expense
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: e821ac9
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-EXPENSE TZ-Tigo-SuperApp-Expense
**Repo:** `TZ-Tigo-SuperApp-Expense` · **Type:** service · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `e821ac9`
**Purpose:** Expenses

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-EXPENSE-001 | POST /api/AdvanceSalary | AdvanceSalaryController.GetHolidayList | — | none | confirmed |
| BE-API-EXPENSE-002 | POST /api/AdvanceSalary | AdvanceSalaryController.GetCompanyConfig | — | none | confirmed |
| BE-API-EXPENSE-003 | POST /api/AdvanceSalary | AdvanceSalaryController.SalaryAdvanceRequest | — | none | confirmed |
| BE-API-EXPENSE-004 | POST /api/AdvanceSalary | AdvanceSalaryController.SalaryAdvanceStop | — | none | confirmed |
| BE-API-EXPENSE-005 | POST /api/AdvanceSalary | AdvanceSalaryController.GetSalaryAdvanceRequests | — | none | confirmed |
| BE-API-EXPENSE-006 | POST /api/AdvanceSalary | AdvanceSalaryController.EditSalaryAdvanceRequest | — | none | confirmed |
| BE-API-EXPENSE-007 | POST /api/ExpenseManagement | ExpenseManagementController.CheckWhitelisted | — | none | confirmed |
| BE-API-EXPENSE-008 | POST /api/ExpenseManagement | ExpenseManagementController.GetInitiatorList | — | none | confirmed |
| BE-API-EXPENSE-009 | POST /api/ExpenseManagement | ExpenseManagementController.BankDetail | — | none | confirmed |
| BE-API-EXPENSE-010 | POST /api/ExpenseManagement | ExpenseManagementController.GetExpense | — | none | confirmed |
| BE-API-EXPENSE-011 | POST /api/ExpenseManagement | ExpenseManagementController.CreateExpense | — | none | confirmed |
| BE-API-EXPENSE-012 | POST /api/ExpenseManagement | ExpenseManagementController.CreateRetirement | — | none | confirmed |
| BE-API-EXPENSE-013 | POST /api/ExpenseManagement | ExpenseManagementController.GetOtherInitiator | — | none | confirmed |
| BE-API-EXPENSE-014 | POST /api/ExpenseManagement | ExpenseManagementController.ChangeInitiator | — | none | confirmed |
| BE-API-EXPENSE-015 | POST /api/ExpenseManagement/enc | ExpenseManagementController.enc | — | none | confirmed |


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
