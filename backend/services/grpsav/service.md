---
kb_section: backend
type: service
ids: [BE-SVC-GRPSAV]
service: GRPSAV
repo: TZ-Tigo-SuperApp-GroupSaving
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: ed4ac20
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-GRPSAV TZ-Tigo-SuperApp-GroupSaving
**Repo:** `TZ-Tigo-SuperApp-GroupSaving` · **Type:** service · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `ed4ac20`
**Purpose:** Group savings

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-GRPSAV-001 | POST /api/Loan | LoanController.GetLoan | — | none | confirmed |
| BE-API-GRPSAV-002 | POST /api/Loan | LoanController.LoanPayment | — | none | confirmed |
| BE-API-GRPSAV-003 | POST /api/Loan | LoanController.OutStandingLoan | — | none | confirmed |
| BE-API-GRPSAV-004 | POST /api/Loan | LoanController.ChangeLoanInterest | — | none | confirmed |
| BE-API-GRPSAV-005 | POST /api/Loan | LoanController.ChangeGuaranteeMode | — | none | confirmed |
| BE-API-GRPSAV-006 | POST /api/Loan | LoanController.ChangeLoanFactor | — | none | confirmed |
| BE-API-GRPSAV-007 | POST /api/Loan | LoanController.ChangeGuarantor | — | none | confirmed |
| BE-API-GRPSAV-008 | POST /api/Loan/encrypt | LoanController.Encrypt | — | none | confirmed |
| BE-API-GRPSAV-009 | POST /api/Loan/decrypt | LoanController.Decrypt | — | none | confirmed |
| BE-API-GRPSAV-010 | POST /api/Loan/EncryptLoanRequest | LoanController.EncryptLoanRequest | — | none | confirmed |
| BE-API-GRPSAV-011 | POST /api/Saving | SavingController.SendContribution | — | none | confirmed |
| BE-API-GRPSAV-012 | POST /api/Saving | SavingController.BuyShares | — | none | confirmed |
| BE-API-GRPSAV-013 | POST /api/Saving | SavingController.Transfer | — | none | confirmed |
| BE-API-GRPSAV-014 | POST /api/Saving | SavingController.QueryMemberPanalPenalties | — | none | confirmed |
| BE-API-GRPSAV-015 | POST /api/Saving | SavingController.PayPanalty | — | none | confirmed |
| BE-API-GRPSAV-016 | POST /api/Saving | SavingController.PaySocialFund | — | none | confirmed |
| BE-API-GRPSAV-017 | POST /api/Saving | SavingController.GetBalanceFee | — | none | confirmed |
| BE-API-GRPSAV-018 | POST /api/Saving | SavingController.GetStatementFee | — | none | confirmed |
| BE-API-GRPSAV-019 | POST /api/Saving | SavingController.ChangeSharePrice | — | none | confirmed |
| BE-API-GRPSAV-020 | POST /api/Saving | SavingController.ChangeBankAccount | — | none | confirmed |
| BE-API-GRPSAV-021 | POST /api/Saving/encrypt | SavingController.Encrypt | — | none | confirmed |
| BE-API-GRPSAV-022 | POST /api/Saving/decrypt | SavingController.Decrypt | — | none | confirmed |
| BE-API-GRPSAV-023 | POST /api/Saving/encSendContribution | SavingController.encTransactionHistory | — | none | confirmed |
| BE-API-GRPSAV-024 | POST /api/Saving/encTransfer | SavingController.encTransactionHistory | — | none | confirmed |
| BE-API-GRPSAV-025 | POST /api/Saving/encQueryMemberPanalties | SavingController.encQueryMemberPanalties | — | none | confirmed |
| BE-API-GRPSAV-026 | POST /api/Saving/encPayPanalty | SavingController.encPayPanalty | — | none | confirmed |
| BE-API-GRPSAV-027 | POST /api/Saving/encPaySocialFund | SavingController.encPayPanalty | — | none | confirmed |
| BE-API-GRPSAV-028 | POST /api/Saving/encGetBalanceFee | SavingController.encPayPanalty | — | none | confirmed |
| BE-API-GRPSAV-029 | POST /api/Saving/encGetStatementFee | SavingController.encGetStatementFee | — | none | confirmed |
| BE-API-GRPSAV-030 | POST /api/Saving/encChangeSharePrice | SavingController.encChangeSharePrice | — | none | confirmed |
| BE-API-GRPSAV-031 | POST /api/Loan | LoanController.GetLoan | — | none | confirmed |
| BE-API-GRPSAV-032 | POST /api/Loan | LoanController.LoanPayment | — | none | confirmed |
| BE-API-GRPSAV-033 | POST /api/Loan | LoanController.OutStandingLoan | — | none | confirmed |
| BE-API-GRPSAV-034 | POST /api/Loan | LoanController.ChangeLoanFactor | — | none | confirmed |
| BE-API-GRPSAV-035 | POST /api/Loan | LoanController.ChangeLoanInterest | — | none | confirmed |
| BE-API-GRPSAV-036 | POST /api/Loan/encrypt | LoanController.Encrypt | — | none | confirmed |
| BE-API-GRPSAV-037 | POST /api/Loan/decrypt | LoanController.Decrypt | — | none | confirmed |
| BE-API-GRPSAV-038 | POST /api/Loan/EncryptLoanRequest | LoanController.EncryptLoanRequest | — | none | confirmed |
| BE-API-GRPSAV-039 | POST /api/Loan/EncryptChangeLoanInterestRequest | LoanController.EncryptChangeLoanInterestRequest | — | none | confirmed |
| BE-API-GRPSAV-040 | POST /api/Group | GroupController.CreateGroup | — | none | confirmed |
| BE-API-GRPSAV-041 | POST /api/Group | GroupController.GeteGroup | — | none | confirmed |
| BE-API-GRPSAV-042 | POST /api/Group | GroupController.AddMember | — | none | confirmed |
| BE-API-GRPSAV-043 | POST /api/Group | GroupController.GetMembersWithRols | — | none | confirmed |
| BE-API-GRPSAV-044 | POST /api/Group | GroupController.GetMembers | — | none | confirmed |
| BE-API-GRPSAV-045 | POST /api/Group | GroupController.GetNotifications | — | none | confirmed |
| BE-API-GRPSAV-046 | POST /api/Group | GroupController.NotificationApproval | — | none | confirmed |
| BE-API-GRPSAV-047 | POST /api/Group | GroupController.RemoveMember | — | none | confirmed |
| BE-API-GRPSAV-048 | POST /api/Group | GroupController.UpdateRole | — | none | confirmed |
| BE-API-GRPSAV-049 | POST /api/Group | GroupController.GetGroupSettings | — | none | confirmed |
| BE-API-GRPSAV-050 | POST /api/Group | GroupController.ChangeApprover | — | none | confirmed |
| BE-API-GRPSAV-051 | POST /api/Group | GroupController.ChangeGroupName | — | none | confirmed |
| BE-API-GRPSAV-052 | POST /api/Group | GroupController.UploadGroupImage | — | none | confirmed |
| BE-API-GRPSAV-053 | POST /api/Group/encrypt | GroupController.Encrypt | — | none | confirmed |
| BE-API-GRPSAV-054 | POST /api/Group/decrypt | GroupController.Decrypt | — | none | confirmed |
| BE-API-GRPSAV-055 | POST /api/Group/encCreateGroup | GroupController.encTransactionHistory | — | none | confirmed |
| BE-API-GRPSAV-056 | POST /api/Group/encGetGroup | GroupController.encTransactionHistory | — | none | confirmed |
| BE-API-GRPSAV-057 | POST /api/Group/encAddMember | GroupController.encTransactionHistory | — | none | confirmed |
| BE-API-GRPSAV-058 | POST /api/Group/encGetMemberWithRols | GroupController.encGetMemberWithRols | — | none | confirmed |
| BE-API-GRPSAV-059 | POST /api/Group/encGetMembers | GroupController.encGetMembers | — | none | confirmed |
| BE-API-GRPSAV-060 | POST /api/Group/encGetNotifications | GroupController.encGetMembers | — | none | confirmed |
| BE-API-GRPSAV-061 | POST /api/Group/encNotificationApproval | GroupController.encNotificationApproval | — | none | confirmed |
| BE-API-GRPSAV-062 | POST /api/Group/encRemoveMember | GroupController.encRemoveMember | — | none | confirmed |
| BE-API-GRPSAV-063 | POST /api/Group/encUpdateRole | GroupController.encUpdateRole | — | none | confirmed |
| BE-API-GRPSAV-064 | POST /api/Group/encGetGroupSettings | GroupController.encGetGroupSettings | — | none | confirmed |
| BE-API-GRPSAV-065 | POST /api/Group/encChangeApprover | GroupController.encChangeApprover | — | none | confirmed |


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
