---
kb_section: backend
type: service
ids: [BE-SVC-LOAN]
service: LOAN
repo: TZ-Tigo-SuperApp-Loan
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 759a471
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-LOAN TZ-Tigo-SuperApp-Loan
**Repo:** `TZ-Tigo-SuperApp-Loan` · **Type:** service · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `759a471`
**Purpose:** Loans

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-LOAN-001 | POST /api/LoanManagement | LoanManagementController.GetLoanInfo | — | none | confirmed |
| BE-API-LOAN-002 | POST /api/LoanManagement | LoanManagementController.SubscribeLoan | — | none | confirmed |
| BE-API-LOAN-003 | POST /api/LoanManagement | LoanManagementController.UnsubscribeLoan | — | none | confirmed |
| BE-API-LOAN-004 | POST /api/LoanManagement | LoanManagementController.GetLoanSummary | — | none | confirmed |
| BE-API-LOAN-005 | POST /api/LoanManagement | LoanManagementController.GetLoanLimit | — | none | confirmed |
| BE-API-LOAN-006 | POST /api/LoanManagement | LoanManagementController.GetLoanTransactions | — | none | confirmed |
| BE-API-LOAN-007 | POST /api/LoanManagement | LoanManagementController.LoanPayment | — | none | confirmed |
| BE-API-LOAN-008 | POST /api/LoanManagement | LoanManagementController.GetLoanSummaryAndLimit | — | none | confirmed |
| BE-API-LOAN-009 | POST /api/Kitonga | KitongaController.KitongaBalanceAndProducts | — | none | confirmed |
| BE-API-LOAN-010 | POST /api/Kitonga | KitongaController.KitongaBalanceAndScore | — | none | confirmed |
| BE-API-LOAN-011 | POST /api/Kitonga | KitongaController.GetCreditScore | — | none | confirmed |
| BE-API-LOAN-012 | POST /api/Kitonga | KitongaController.GetCustomerLoanProducts | — | none | confirmed |
| BE-API-LOAN-013 | POST /api/Kitonga | KitongaController.CheckLoanEligibility | — | none | confirmed |
| BE-API-LOAN-014 | POST /api/Kitonga | KitongaController.PurchaseLoanProduct | — | none | confirmed |
| BE-API-LOAN-015 | POST /api/Kitonga | KitongaController.QueryOutstandingLoan | — | none | confirmed |
| BE-API-LOAN-016 | POST /api/Kitonga | KitongaController.CreditScoreAndOutstandingLoan | — | none | confirmed |
| BE-API-LOAN-017 | POST /api/Kitonga | KitongaController.SubmitRepayLoan | — | none | confirmed |
| BE-API-LOAN-018 | POST /api/Kitonga | KitongaController.LoanInstallment | — | none | confirmed |
| BE-API-LOAN-019 | POST /api/Kitonga | KitongaController.RepaymentHistory | — | none | confirmed |
| BE-API-LOAN-020 | POST /api/Kitonga/enc | KitongaController.enc | — | none | confirmed |
| BE-API-LOAN-021 | POST /api/Kitonga/dec | KitongaController.dec | — | none | confirmed |
| BE-API-LOAN-022 | POST /api/DeviceLoan | DeviceLoanController.GetOutstandingLoan | — | none | confirmed |
| BE-API-LOAN-023 | POST /api/DeviceLoan | DeviceLoanController.SubmitLoanRepayment | — | none | confirmed |
| BE-API-LOAN-024 | POST /api/DeviceLoan/enc | DeviceLoanController.enc | — | none | confirmed |


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
Status this run: **inventoried**
