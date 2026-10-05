---
kb_section: backend
type: service
ids: [BE-SVC-LOAN]
service: LOAN
repo: TZ-Tigo-SuperApp-Loan
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 759a471
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-LOAN Loans (device / Kitonga)
**Repo:** `TZ-Tigo-SuperApp-Loan` · **Type:** service · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `759a471`
**Purpose:** Loans (device / Kitonga)

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** MassTransit.RabbitMQ, Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-LOAN-001 | `POST /api/LoanManagement/GetLoanInfo` | `LoanManagementController.GetLoanInfo` | LoanManagementController.GetLoanInfo | see contract | confirmed |
| BE-API-LOAN-002 | `POST /api/LoanManagement/SubscribeLoan` | `LoanManagementController.SubscribeLoan` | LoanManagementController.SubscribeLoan | see contract | confirmed |
| BE-API-LOAN-003 | `POST /api/LoanManagement/UnsubscribeLoan` | `LoanManagementController.UnsubscribeLoan` | LoanManagementController.UnsubscribeLoan | see contract | confirmed |
| BE-API-LOAN-004 | `POST /api/LoanManagement/GetLoanSummary` | `LoanManagementController.GetLoanSummary` | LoanManagementController.GetLoanSummary | see contract | confirmed |
| BE-API-LOAN-005 | `POST /api/LoanManagement/GetLoanLimit` | `LoanManagementController.GetLoanLimit` | LoanManagementController.GetLoanLimit | see contract | confirmed |
| BE-API-LOAN-006 | `POST /api/LoanManagement/GetLoanTransactions` | `LoanManagementController.GetLoanTransactions` | LoanManagementController.GetLoanTransactions | see contract | confirmed |
| BE-API-LOAN-007 | `POST /api/LoanManagement/LoanPayment` | `LoanManagementController.LoanPayment` | LoanManagementController.LoanPayment | see contract | confirmed |
| BE-API-LOAN-008 | `POST /api/LoanManagement/GetLoanSummaryAndLimit` | `LoanManagementController.GetLoanSummaryAndLimit` | LoanManagementController.GetLoanSummaryAndLimit | see contract | confirmed |
| BE-API-LOAN-009 | `POST /api/Kitonga/KitongaBalanceAndProducts` | `KitongaController.KitongaBalanceAndProducts` | KitongaController.KitongaBalanceAndProducts | see contract | confirmed |
| BE-API-LOAN-010 | `POST /api/Kitonga/KitongaBalanceAndScore` | `KitongaController.KitongaBalanceAndScore` | KitongaController.KitongaBalanceAndScore | see contract | confirmed |
| BE-API-LOAN-011 | `POST /api/Kitonga/GetCreditScore` | `KitongaController.GetCreditScore` | KitongaController.GetCreditScore | see contract | confirmed |
| BE-API-LOAN-012 | `POST /api/Kitonga/GetCustomerLoanProducts` | `KitongaController.GetCustomerLoanProducts` | KitongaController.GetCustomerLoanProducts | see contract | confirmed |
| BE-API-LOAN-013 | `POST /api/Kitonga/CheckLoanEligibility` | `KitongaController.CheckLoanEligibility` | KitongaController.CheckLoanEligibility | see contract | confirmed |
| BE-API-LOAN-014 | `POST /api/Kitonga/PurchaseLoanProduct` | `KitongaController.PurchaseLoanProduct` | KitongaController.PurchaseLoanProduct | see contract | confirmed |
| BE-API-LOAN-015 | `POST /api/Kitonga/QueryOutstandingLoan` | `KitongaController.QueryOutstandingLoan` | KitongaController.QueryOutstandingLoan | see contract | confirmed |
| BE-API-LOAN-016 | `POST /api/Kitonga/CreditScoreAndOutstandingLoan` | `KitongaController.CreditScoreAndOutstandingLoan` | KitongaController.CreditScoreAndOutstandingLoan | see contract | confirmed |
| BE-API-LOAN-017 | `POST /api/Kitonga/SubmitRepayLoan` | `KitongaController.SubmitRepayLoan` | KitongaController.SubmitRepayLoan | see contract | confirmed |
| BE-API-LOAN-018 | `POST /api/Kitonga/LoanInstallment` | `KitongaController.LoanInstallment` | KitongaController.LoanInstallment | see contract | confirmed |
| BE-API-LOAN-019 | `POST /api/Kitonga/RepaymentHistory` | `KitongaController.RepaymentHistory` | KitongaController.RepaymentHistory | see contract | confirmed |
| BE-API-LOAN-020 | `POST /api/Kitonga/enc` | `KitongaController.enc` | KitongaController.enc | see contract | confirmed |
| BE-API-LOAN-021 | `POST /api/Kitonga/dec` | `KitongaController.dec` | KitongaController.dec | see contract | partial |
| BE-API-LOAN-022 | `POST /api/DeviceLoan/GetOutstandingLoan` | `DeviceLoanController.GetOutstandingLoan` | DeviceLoanController.GetOutstandingLoan | see contract | confirmed |
| BE-API-LOAN-023 | `POST /api/DeviceLoan/SubmitLoanRepayment` | `DeviceLoanController.SubmitLoanRepayment` | DeviceLoanController.SubmitLoanRepayment | see contract | confirmed |
| BE-API-LOAN-024 | `POST /api/DeviceLoan/enc` | `DeviceLoanController.enc` | DeviceLoanController.enc | see contract | confirmed |

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
| `BaseEntity` / `—` | `TZTigoSuperAppLoan/Data/Entities/BaseEntity.cs` |
| `KitongaLoanRepository` / `—` | `TZTigoSuperAppLoan/Domain/Repositories/KitongaLoanRepository.cs` |
| `LoanManagementRepository` / `—` | `TZTigoSuperAppLoan/Domain/Repositories/LoanManagementRepository.cs` |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`ConfigAPIUrl`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `EnableLog:Warning`, `Encryption_Decryption_Key`, `GrantType`, `IV`, `IsRedisCluster`, `KitongAuthToken`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:LogQueueName`, `RabbitMQ:LogURL`, `RabbitMQ:Username`, `RedisPassword (key name)<redacted-purpose>`, `RedisURL`, `SaveLogs`, `SendAuditLogsViaService`, `Tanzania:<redacted-purpose>`, `Tanzania:Certificate`, `Tanzania:ChannelId`, `Tanzania:ChannelPass`, `Tanzania:ChannelUser`, `Tanzania:ConsumerID`, `Tanzania:CountryCode`, `Tanzania:GetLoanInformation`, `Tanzania:GetOutstandingLoan`, `Tanzania:LoanLimit`, `Tanzania:PayLoan`, `Tanzania:SubscribeLoan`, `Tanzania:SuperAppCheckLoanEligibility`, `Tanzania:SuperAppCreditScore`, `Tanzania:SuperAppCustomerRepaymentHistory`, `Tanzania:SuperAppDeviceLoanDetails`, `Tanzania:SuperAppDeviceLoanRepayment`, `Tanzania:SuperAppDeviceToken`, `Tanzania:SuperAppGetCustomerLoanProducts`, `Tanzania:SuperAppKitongaGetToken`, `Tanzania:SuperAppLoanInstalment`, `Tanzania:SuperAppPurchaseLoanProduct`

## Open questions
- Gateway public URLs not in-repo.
