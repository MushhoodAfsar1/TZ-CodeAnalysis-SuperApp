---
kb_section: backend
type: service
ids: [BE-SVC-GRPSAV]
service: GRPSAV
repo: TZ-Tigo-SuperApp-GroupSaving
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: ed4ac20
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-GRPSAV Group savings and group loans
**Repo:** `TZ-Tigo-SuperApp-GroupSaving` · **Type:** service · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `ed4ac20`
**Purpose:** Group savings and group loans

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** MassTransit.RabbitMQ, Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-GRPSAV-001 | `POST /api/Loan/GetLoan` | `LoanController.GetLoan` | LoanController.GetLoan | see contract | confirmed |
| BE-API-GRPSAV-002 | `POST /api/Loan/LoanPayment` | `LoanController.LoanPayment` | LoanController.LoanPayment | see contract | confirmed |
| BE-API-GRPSAV-003 | `POST /api/Loan/OutStandingLoan` | `LoanController.OutStandingLoan` | LoanController.OutStandingLoan | see contract | confirmed |
| BE-API-GRPSAV-004 | `POST /api/Loan/ChangeLoanInterest` | `LoanController.ChangeLoanInterest` | LoanController.ChangeLoanInterest | see contract | confirmed |
| BE-API-GRPSAV-005 | `POST /api/Loan/ChangeGuaranteeMode` | `LoanController.ChangeGuaranteeMode` | LoanController.ChangeGuaranteeMode | see contract | confirmed |
| BE-API-GRPSAV-006 | `POST /api/Loan/ChangeLoanFactor` | `LoanController.ChangeLoanFactor` | LoanController.ChangeLoanFactor | see contract | confirmed |
| BE-API-GRPSAV-007 | `POST /api/Loan/ChangeGuarantor` | `LoanController.ChangeGuarantor` | LoanController.ChangeGuarantor | see contract | confirmed |
| BE-API-GRPSAV-008 | `POST /api/Loan/encrypt` | `LoanController.Encrypt` | LoanController.Encrypt | see contract | confirmed |
| BE-API-GRPSAV-009 | `POST /api/Loan/decrypt` | `LoanController.Decrypt` | LoanController.Decrypt | see contract | confirmed |
| BE-API-GRPSAV-010 | `POST /api/Loan/EncryptLoanRequest` | `LoanController.EncryptLoanRequest` | LoanController.EncryptLoanRequest | see contract | confirmed |
| BE-API-GRPSAV-011 | `POST /api/Saving/SendContribution` | `SavingController.SendContribution` | SavingController.SendContribution | see contract | confirmed |
| BE-API-GRPSAV-012 | `POST /api/Saving/BuyShares` | `SavingController.BuyShares` | SavingController.BuyShares | see contract | confirmed |
| BE-API-GRPSAV-013 | `POST /api/Saving/Transfer` | `SavingController.Transfer` | SavingController.Transfer | see contract | confirmed |
| BE-API-GRPSAV-014 | `POST /api/Saving/QueryMemberPanalPenalties` | `SavingController.QueryMemberPanalPenalties` | SavingController.QueryMemberPanalPenalties | see contract | confirmed |
| BE-API-GRPSAV-015 | `POST /api/Saving/PayPanalty` | `SavingController.PayPanalty` | SavingController.PayPanalty | see contract | confirmed |
| BE-API-GRPSAV-016 | `POST /api/Saving/PaySocialFund` | `SavingController.PaySocialFund` | SavingController.PaySocialFund | see contract | confirmed |
| BE-API-GRPSAV-017 | `POST /api/Saving/GetBalanceFee` | `SavingController.GetBalanceFee` | SavingController.GetBalanceFee | see contract | confirmed |
| BE-API-GRPSAV-018 | `POST /api/Saving/GetStatementFee` | `SavingController.GetStatementFee` | SavingController.GetStatementFee | see contract | confirmed |
| BE-API-GRPSAV-019 | `POST /api/Saving/ChangeSharePrice` | `SavingController.ChangeSharePrice` | SavingController.ChangeSharePrice | see contract | confirmed |
| BE-API-GRPSAV-020 | `POST /api/Saving/ChangeBankAccount` | `SavingController.ChangeBankAccount` | SavingController.ChangeBankAccount | see contract | confirmed |
| BE-API-GRPSAV-021 | `POST /api/Saving/encrypt` | `SavingController.Encrypt` | SavingController.Encrypt | see contract | confirmed |
| BE-API-GRPSAV-022 | `POST /api/Saving/decrypt` | `SavingController.Decrypt` | SavingController.Decrypt | see contract | confirmed |
| BE-API-GRPSAV-023 | `POST /api/Saving/encSendContribution` | `SavingController.encTransactionHistory` | SavingController.encTransactionHistory | see contract | confirmed |
| BE-API-GRPSAV-024 | `POST /api/Saving/encTransfer` | `SavingController.encTransactionHistory` | SavingController.encTransactionHistory | see contract | confirmed |
| BE-API-GRPSAV-025 | `POST /api/Saving/encQueryMemberPanalties` | `SavingController.encQueryMemberPanalties` | SavingController.encQueryMemberPanalties | see contract | confirmed |
| BE-API-GRPSAV-026 | `POST /api/Saving/encPayPanalty` | `SavingController.encPayPanalty` | SavingController.encPayPanalty | see contract | confirmed |
| BE-API-GRPSAV-027 | `POST /api/Saving/encPaySocialFund` | `SavingController.encPayPanalty` | SavingController.encPayPanalty | see contract | confirmed |
| BE-API-GRPSAV-028 | `POST /api/Saving/encGetBalanceFee` | `SavingController.encPayPanalty` | SavingController.encPayPanalty | see contract | confirmed |
| BE-API-GRPSAV-029 | `POST /api/Saving/encGetStatementFee` | `SavingController.encGetStatementFee` | SavingController.encGetStatementFee | see contract | confirmed |
| BE-API-GRPSAV-030 | `POST /api/Saving/encChangeSharePrice` | `SavingController.encChangeSharePrice` | SavingController.encChangeSharePrice | see contract | confirmed |
| BE-API-GRPSAV-031 | `POST /api/Group/CreateGroup` | `GroupController.CreateGroup` | GroupController.CreateGroup | see contract | confirmed |
| BE-API-GRPSAV-032 | `POST /api/Group/GetGroups` | `GroupController.GeteGroup` | GroupController.GeteGroup | see contract | confirmed |
| BE-API-GRPSAV-033 | `POST /api/Group/AddMember` | `GroupController.AddMember` | GroupController.AddMember | see contract | confirmed |
| BE-API-GRPSAV-034 | `POST /api/Group/GetMembersWithRols` | `GroupController.GetMembersWithRols` | GroupController.GetMembersWithRols | see contract | confirmed |
| BE-API-GRPSAV-035 | `POST /api/Group/GetMembers` | `GroupController.GetMembers` | GroupController.GetMembers | see contract | confirmed |
| BE-API-GRPSAV-036 | `POST /api/Group/GetNotifications` | `GroupController.GetNotifications` | GroupController.GetNotifications | see contract | confirmed |
| BE-API-GRPSAV-037 | `POST /api/Group/NotificationApproval` | `GroupController.NotificationApproval` | GroupController.NotificationApproval | see contract | confirmed |
| BE-API-GRPSAV-038 | `POST /api/Group/RemoveMember` | `GroupController.RemoveMember` | GroupController.RemoveMember | see contract | confirmed |
| BE-API-GRPSAV-039 | `POST /api/Group/UpdateRole` | `GroupController.UpdateRole` | GroupController.UpdateRole | see contract | confirmed |
| BE-API-GRPSAV-040 | `POST /api/Group/GetGroupSettings` | `GroupController.GetGroupSettings` | GroupController.GetGroupSettings | see contract | confirmed |
| BE-API-GRPSAV-041 | `POST /api/Group/ChangeApprover` | `GroupController.ChangeApprover` | GroupController.ChangeApprover | see contract | confirmed |
| BE-API-GRPSAV-042 | `POST /api/Group/ChangeGroupName` | `GroupController.ChangeGroupName` | GroupController.ChangeGroupName | see contract | confirmed |
| BE-API-GRPSAV-043 | `POST /api/Group/UploadGroupImage` | `GroupController.UploadGroupImage` | GroupController.UploadGroupImage | see contract | confirmed |
| BE-API-GRPSAV-044 | `POST /api/Group/encrypt` | `GroupController.Encrypt` | GroupController.Encrypt | see contract | confirmed |
| BE-API-GRPSAV-045 | `POST /api/Group/decrypt` | `GroupController.Decrypt` | GroupController.Decrypt | see contract | confirmed |
| BE-API-GRPSAV-046 | `POST /api/Group/encCreateGroup` | `GroupController.encTransactionHistory` | GroupController.encTransactionHistory | see contract | confirmed |
| BE-API-GRPSAV-047 | `POST /api/Group/encGetGroup` | `GroupController.encTransactionHistory` | GroupController.encTransactionHistory | see contract | confirmed |
| BE-API-GRPSAV-048 | `POST /api/Group/encAddMember` | `GroupController.encTransactionHistory` | GroupController.encTransactionHistory | see contract | confirmed |
| BE-API-GRPSAV-049 | `POST /api/Group/encGetMemberWithRols` | `GroupController.encGetMemberWithRols` | GroupController.encGetMemberWithRols | see contract | confirmed |
| BE-API-GRPSAV-050 | `POST /api/Group/encGetMembers` | `GroupController.encGetMembers` | GroupController.encGetMembers | see contract | confirmed |
| BE-API-GRPSAV-051 | `POST /api/Group/encGetNotifications` | `GroupController.encGetMembers` | GroupController.encGetMembers | see contract | confirmed |
| BE-API-GRPSAV-052 | `POST /api/Group/encNotificationApproval` | `GroupController.encNotificationApproval` | GroupController.encNotificationApproval | see contract | confirmed |
| BE-API-GRPSAV-053 | `POST /api/Group/encRemoveMember` | `GroupController.encRemoveMember` | GroupController.encRemoveMember | see contract | confirmed |
| BE-API-GRPSAV-054 | `POST /api/Group/encUpdateRole` | `GroupController.encUpdateRole` | GroupController.encUpdateRole | see contract | confirmed |
| BE-API-GRPSAV-055 | `POST /api/Group/encGetGroupSettings` | `GroupController.encGetGroupSettings` | GroupController.encGetGroupSettings | see contract | confirmed |
| BE-API-GRPSAV-056 | `POST /api/Group/encChangeApprover` | `GroupController.encChangeApprover` | GroupController.encChangeApprover | see contract | confirmed |
| BE-API-GRPSAV-057 | `POST /api/Loan/GetLoan` | `LoanController.GetLoan` | LoanController.GetLoan | see contract | confirmed |
| BE-API-GRPSAV-058 | `POST /api/Loan/LoanPayment` | `LoanController.LoanPayment` | LoanController.LoanPayment | see contract | confirmed |
| BE-API-GRPSAV-059 | `POST /api/Loan/OutStandingLoan` | `LoanController.OutStandingLoan` | LoanController.OutStandingLoan | see contract | confirmed |
| BE-API-GRPSAV-060 | `POST /api/Loan/ChangeLoanFactor` | `LoanController.ChangeLoanFactor` | LoanController.ChangeLoanFactor | see contract | confirmed |
| BE-API-GRPSAV-061 | `POST /api/Loan/ChangeLoanInterest` | `LoanController.ChangeLoanInterest` | LoanController.ChangeLoanInterest | see contract | confirmed |
| BE-API-GRPSAV-062 | `POST /api/Loan/encrypt` | `LoanController.Encrypt` | LoanController.Encrypt | see contract | confirmed |
| BE-API-GRPSAV-063 | `POST /api/Loan/decrypt` | `LoanController.Decrypt` | LoanController.Decrypt | see contract | confirmed |
| BE-API-GRPSAV-064 | `POST /api/Loan/EncryptLoanRequest` | `LoanController.EncryptLoanRequest` | LoanController.EncryptLoanRequest | see contract | confirmed |
| BE-API-GRPSAV-065 | `POST /api/Loan/EncryptChangeLoanInterestRequest` | `LoanController.EncryptChangeLoanInterestRequest` | LoanController.EncryptChangeLoanInterestRequest | see contract | confirmed |

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
| `TZExternalPaymentEFContext` / `—` | `TZTigoSuperAppGroupSaving/Domain/DBContext/TZExternalPaymentEFContext.cs` |
| `AccountEFContext` / `—` | `TZTigoSuperAppGroupSaving/Domain/DBContext/AccountEFContext.cs` |
| `Tokens` / `—` | `TZTigoSuperAppGroupSaving/Domain/Entity/Tokens.cs` |
| `BillPayment` / `—` | `TZTigoSuperAppGroupSaving/Domain/Entity/BillPayment.cs` |
| `BaseEntity` / `—` | `TZTigoSuperAppGroupSaving/Domain/Entity/BaseEntity.cs` |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`ConfigAPIUrl`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `EnableLog:Warning`, `Encryption_Decryption_Key`, `FCMNotify`, `IV`, `IsRedisCluster`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:LogQueueName`, `RabbitMQ:LogURL`, `RabbitMQ:Username`, `RedisPassword (key name)<redacted-purpose>`, `RedisURL`, `SaveLogs`, `SendAuditLogsViaService`, `SendFCMViaService`, `Tanzania:<redacted-purpose>`, `Tanzania:BaseUrl`, `Tanzania:GSAddMember`, `Tanzania:GSApplyLoan`, `Tanzania:GSApproveNotification`, `Tanzania:GSBuyShares`, `Tanzania:GSChangeApproversMode`, `Tanzania:GSChangeLoanFactor`, `Tanzania:GSChangeLoanInterest`, `Tanzania:GSChangeSharePrice`, `Tanzania:GSContribute`, `Tanzania:GSCreateGroup`, `Tanzania:GSGetBalanceFee`, `Tanzania:GSGetGroupSettings`, `Tanzania:GSGetGroups`, `Tanzania:GSGetLoans`, `Tanzania:GSGetMemberPenalties`, `Tanzania:GSGetMemberRoles`, `Tanzania:GSGetMembersList`, `Tanzania:GSGetNotification`, `Tanzania:GSGetStatementFee`, `Tanzania:GSPayLoan`

## Open questions
- Gateway public URLs not in-repo.
