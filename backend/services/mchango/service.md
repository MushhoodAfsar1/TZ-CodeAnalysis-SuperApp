---
kb_section: backend
type: service
ids: [BE-SVC-MCHANGO]
service: MCHANGO
repo: TZ-Tigo-SuperApp-MChango
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 7c288ab
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-MCHANGO TZ-Tigo-SuperApp-MChango
**Repo:** `TZ-Tigo-SuperApp-MChango` · **Type:** service · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `7c288ab`
**Purpose:** MChango collections

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-MCHANGO-001 | POST /api/web/Auth/login | AuthController.LoginAsync | — | none | confirmed |
| BE-API-MCHANGO-002 | POST /api/web/Account/GetAllActiveAccounts | AccountController.GetMyMchangoAccounts | — | none | confirmed |
| BE-API-MCHANGO-003 | POST /api/web/Account/ChangeAccountPaymentStatus | AccountController.ChangeAccountPaymentStatus | — | none | confirmed |
| BE-API-MCHANGO-004 | POST /api/web/Account/SendMchangoNotfication | AccountController.SendMchangoNotfication | — | none | confirmed |
| BE-API-MCHANGO-005 | POST /api/mobile/Notification/SendReminder | NotificationController.SendRemiders | — | none | confirmed |
| BE-API-MCHANGO-006 | POST /api/mobile/Notification/AddNotification | NotificationController.AddNotification | — | none | confirmed |
| BE-API-MCHANGO-007 | POST /api/mobile/Notification/GetAllNotification | NotificationController.GetAllNotification | — | none | confirmed |
| BE-API-MCHANGO-008 | POST /api/mobile/Notification/SendMchangoNotfication | NotificationController.SendMchangoNotfication | — | none | confirmed |
| BE-API-MCHANGO-009 | POST /api/mobile/Purpose/CreatePurpose | PurposeController.CreatePurpose | — | none | confirmed |
| BE-API-MCHANGO-010 | POST /api/mobile/Purpose/GetPurpose | PurposeController.GetPurpose | — | none | confirmed |
| BE-API-MCHANGO-011 | POST /api/mobile/Purpose/GetAllPurposes | PurposeController.GetAllPurposes | — | none | confirmed |
| BE-API-MCHANGO-012 | POST /api/mobile/Purpose/UpdatePurpose | PurposeController.UpdatePurpose | — | none | confirmed |
| BE-API-MCHANGO-013 | POST /api/mobile/Purpose/DeletePurpose | PurposeController.DeletePurpose | — | none | confirmed |
| BE-API-MCHANGO-014 | POST /api/mobile/Invitation/CreateEvent | InvitationController.CreateEvent | — | none | confirmed |
| BE-API-MCHANGO-015 | POST /api/mobile/Invitation/UpdateEvent | InvitationController.UpdateEvent | — | none | confirmed |
| BE-API-MCHANGO-016 | POST /api/mobile/Invitation/GetEventById | InvitationController.GetEventById | — | none | confirmed |
| BE-API-MCHANGO-017 | POST /api/mobile/Invitation/GetAllEvents | InvitationController.GetAllEvents | — | none | confirmed |
| BE-API-MCHANGO-018 | POST /api/mobile/Invitation/DeleteEventById | InvitationController.DeleteEventById | — | none | confirmed |
| BE-API-MCHANGO-019 | POST /api/mobile/Invitation/CreateInvitation | InvitationController.CreateInvitation | — | none | confirmed |
| BE-API-MCHANGO-020 | POST /api/mobile/Invitation/ValidateInvitationCode | InvitationController.ValidateInvitationCode | — | none | confirmed |
| BE-API-MCHANGO-021 | POST /api/mobile/Invitation/RedeemInvitationCode | InvitationController.RedeemInvitationCode | — | none | confirmed |
| BE-API-MCHANGO-022 | POST /api/mobile/Invitation/GetAllInvitation | InvitationController.GetAllInvitation | — | none | confirmed |
| BE-API-MCHANGO-023 | POST /api/mobile/Invitation/GetInvitationHistory | InvitationController.GetInvitationHistory | — | none | confirmed |
| BE-API-MCHANGO-024 | POST /api/mobile/Account/GetMyMchangoAccounts | AccountController.GetMyMchangoAccounts | — | none | confirmed |
| BE-API-MCHANGO-025 | POST /api/mobile/Account/GetMyMchangoAccountDetails | AccountController.GetMyMchangoAccountDetails | — | none | confirmed |
| BE-API-MCHANGO-026 | POST /api/mobile/Account/CreateAccount | AccountController.CreateAccount | — | none | confirmed |
| BE-API-MCHANGO-027 | POST /api/mobile/Account/CloseMchangoAccount | AccountController.CloseMchangoAccount | — | none | confirmed |
| BE-API-MCHANGO-028 | POST /api/mobile/Account/ChangeAccountRole | AccountController.ChangeAccountRole | — | none | confirmed |
| BE-API-MCHANGO-029 | POST /api/mobile/Account/CreateAccountRole | AccountController.CreateAccountRole | — | none | confirmed |
| BE-API-MCHANGO-030 | POST /api/mobile/Account/GetAllRoleByAccount | AccountController.GetAllRoleByAccount | — | none | confirmed |
| BE-API-MCHANGO-031 | POST /api/mobile/Account/DeleteAccountRole | AccountController.DeleteAccountRole | — | none | confirmed |
| BE-API-MCHANGO-032 | POST /api/mobile/Account/GetMyMchangoAccountPurposeAndDuration | AccountController.GetMyMchangoAccountPurposeAndDuration | — | none | confirmed |
| BE-API-MCHANGO-033 | POST /api/mobile/SelfCare/CheckPinStatus | SelfCareController.CheckPinStatus | — | none | confirmed |
| BE-API-MCHANGO-034 | POST /api/mobile/SelfCare/ChangePIN | SelfCareController.ChangePIN | — | none | confirmed |
| BE-API-MCHANGO-035 | POST /api/web/Encryption/encrypt | EncryptionController.EncryptAsync | — | JWT | confirmed |
| BE-API-MCHANGO-036 | POST /api/web/Encryption/decrypt | EncryptionController.DecryptAsync | — | JWT | confirmed |
| BE-API-MCHANGO-037 | POST /api/mobile/MobileAppReports/GetMyReport | MobileAppReportsController.GetMyReport | — | none | confirmed |
| BE-API-MCHANGO-038 | GET /api/web/AccountReports/GetMyMchangoAccountReport | AccountReportsController.GetMyMchangoAccountReport | — | none | confirmed |
| BE-API-MCHANGO-039 | GET /api/web/AccountReports/GetGroupBalanceReport | AccountReportsController.GetGroupBalanceReport | — | none | confirmed |
| BE-API-MCHANGO-040 | GET /api/web/AccountReports/GetMyMchangoAccountStatementReport | AccountReportsController.GetMyMchangoAccountStatementReport | — | none | confirmed |
| BE-API-MCHANGO-041 | POST /api/mobile/RTT/CreateRTT | RTTController.CreateRTT | — | none | confirmed |
| BE-API-MCHANGO-042 | POST /api/mobile/Transaction/InitiatePledgeTransaction | TransactionController.InitiatePledgeTransaction | — | none | confirmed |
| BE-API-MCHANGO-043 | POST /api/mobile/Transaction/GetMyPledgeTransactions | TransactionController.GetMyPledgeTransactions | — | none | confirmed |
| BE-API-MCHANGO-044 | POST /api/mobile/Transaction/GetMyContributions | TransactionController.GetMyContributions | — | none | confirmed |
| BE-API-MCHANGO-045 | POST /api/mobile/Transaction/GetMyTransactions | TransactionController.GetMyTransactions | — | none | confirmed |
| BE-API-MCHANGO-046 | POST /api/mobile/Transaction/SendMoneyFeeCheck | TransactionController.SendMoneyFeeCheck | — | none | confirmed |
| BE-API-MCHANGO-047 | POST /api/mobile/Transaction/SendMoneySubmit | TransactionController.SendMoneySubmit | — | none | confirmed |
| BE-API-MCHANGO-048 | POST /api/mobile/Transaction/LipaFeeCheck | TransactionController.LipaFeeCheck | — | none | confirmed |
| BE-API-MCHANGO-049 | POST /api/mobile/Transaction/LipaInitiateTransaction | TransactionController.LipaInitiateTransaction | — | none | confirmed |
| BE-API-MCHANGO-050 | POST /api/mobile/Transaction/MchangoFeeCheck | TransactionController.MchangoFeeCheck | — | none | confirmed |
| BE-API-MCHANGO-051 | POST /api/mobile/Transaction/ContributeInitiateTransaction | TransactionController.MchangoInitiateTransaction | — | none | confirmed |
| BE-API-MCHANGO-052 | POST /api/mobile/Transaction/CashoutPayment | TransactionController.CashoutPayment | — | none | confirmed |
| BE-API-MCHANGO-053 | POST /api/mobile/Transaction/CashoutFee | TransactionController.CashoutFee | — | none | confirmed |
| BE-API-MCHANGO-054 | POST /api/mobile/Transaction/BankTransferFee | TransactionController.BankTransferFee | — | none | confirmed |
| BE-API-MCHANGO-055 | POST /api/mobile/Transaction/BankTransferPayment | TransactionController.BankTransferPayment | — | none | confirmed |
| BE-API-MCHANGO-056 | POST /api/mobile/Transaction/MchangoCashoutFee | TransactionController.MchangoCashoutFee | — | none | confirmed |
| BE-API-MCHANGO-057 | GET /api/web/ChangeAccountGroup/GetAllAccount | ChangeAccountGroupController.GetAllAccount | — | none | confirmed |
| BE-API-MCHANGO-058 | GET /api/web/ChangeAccountGroup/ChangeGroup | ChangeAccountGroupController.ChangeGroup | — | none | confirmed |
| BE-API-MCHANGO-059 | POST /api/web/ChangeAccountGroup/ChangeGroup | ChangeAccountGroupController.ChangeGroupPost | — | none | confirmed |
| BE-API-MCHANGO-060 | POST /api/mobile/AccountDurationType/CreateAccountDurationType | AccountDurationTypeController.CreateAccountDurationType | — | none | confirmed |
| BE-API-MCHANGO-061 | POST /api/mobile/AccountDurationType/GetAccountDurationType | AccountDurationTypeController.GetAccountDurationType | — | none | confirmed |
| BE-API-MCHANGO-062 | POST /api/mobile/AccountDurationType/GetAllAccountDurationTypes | AccountDurationTypeController.GetAllAccountDurationTypes | — | none | confirmed |
| BE-API-MCHANGO-063 | POST /api/mobile/AccountDurationType/UpdateAccountDurationType | AccountDurationTypeController.UpdateAccountDurationType | — | none | confirmed |
| BE-API-MCHANGO-064 | POST /api/mobile/AccountDurationType/DeleteAccountDurationType | AccountDurationTypeController.DeleteAccountDurationType | — | none | confirmed |


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
