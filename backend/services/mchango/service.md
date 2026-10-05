---
kb_section: backend
type: service
ids: [BE-SVC-MCHANGO]
service: MCHANGO
repo: TZ-Tigo-SuperApp-MChango
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 7c288ab
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-MCHANGO MChango collections (mobile + web)
**Repo:** `TZ-Tigo-SuperApp-MChango` · **Type:** service · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `7c288ab`
**Purpose:** MChango collections (mobile + web)

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** FluentValidation, FluentValidation.AspNetCore, Microsoft.AspNetCore.Authentication.JwtBearer, Microsoft.AspNetCore.Identity.EntityFrameworkCore, Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, RabbitMQ.Client, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-MCHANGO-001 | `POST /api/mobile/RTT/CreateRTT` | `RTTController.CreateRTT` | RTTController.CreateRTT | see contract | confirmed |
| BE-API-MCHANGO-002 | `POST /api/mobile/Purpose/CreatePurpose` | `PurposeController.CreatePurpose` | PurposeController.CreatePurpose | see contract | confirmed |
| BE-API-MCHANGO-003 | `POST /api/mobile/Purpose/GetPurpose` | `PurposeController.GetPurpose` | PurposeController.GetPurpose | see contract | confirmed |
| BE-API-MCHANGO-004 | `POST /api/mobile/Purpose/GetAllPurposes` | `PurposeController.GetAllPurposes` | PurposeController.GetAllPurposes | see contract | confirmed |
| BE-API-MCHANGO-005 | `POST /api/mobile/Purpose/UpdatePurpose` | `PurposeController.UpdatePurpose` | PurposeController.UpdatePurpose | see contract | confirmed |
| BE-API-MCHANGO-006 | `POST /api/mobile/Purpose/DeletePurpose` | `PurposeController.DeletePurpose` | PurposeController.DeletePurpose | see contract | confirmed |
| BE-API-MCHANGO-007 | `GET /api/web/ChangeAccountGroup/GetAllAccount` | `ChangeAccountGroupController.GetAllAccount` | ChangeAccountGroupController.GetAllAccount | see contract | confirmed |
| BE-API-MCHANGO-008 | `GET /api/web/ChangeAccountGroup/ChangeGroup` | `ChangeAccountGroupController.ChangeGroup` | ChangeAccountGroupController.ChangeGroup | see contract | confirmed |
| BE-API-MCHANGO-009 | `POST /api/web/ChangeAccountGroup/ChangeGroup` | `ChangeAccountGroupController.ChangeGroupPost` | ChangeAccountGroupController.ChangeGroupPost | see contract | confirmed |
| BE-API-MCHANGO-010 | `POST /api/mobile/AccountDurationType/CreateAccountDurationType` | `AccountDurationTypeController.CreateAccountDurationType` | AccountDurationTypeController.CreateAccountDurationType | see contract | confirmed |
| BE-API-MCHANGO-011 | `POST /api/mobile/AccountDurationType/GetAccountDurationType` | `AccountDurationTypeController.GetAccountDurationType` | AccountDurationTypeController.GetAccountDurationType | see contract | confirmed |
| BE-API-MCHANGO-012 | `POST /api/mobile/AccountDurationType/GetAllAccountDurationTypes` | `AccountDurationTypeController.GetAllAccountDurationTypes` | AccountDurationTypeController.GetAllAccountDurationTypes | see contract | confirmed |
| BE-API-MCHANGO-013 | `POST /api/mobile/AccountDurationType/UpdateAccountDurationType` | `AccountDurationTypeController.UpdateAccountDurationType` | AccountDurationTypeController.UpdateAccountDurationType | see contract | confirmed |
| BE-API-MCHANGO-014 | `POST /api/mobile/AccountDurationType/DeleteAccountDurationType` | `AccountDurationTypeController.DeleteAccountDurationType` | AccountDurationTypeController.DeleteAccountDurationType | see contract | confirmed |
| BE-API-MCHANGO-015 | `POST /api/mobile/Notification/SendReminder` | `NotificationController.SendRemiders` | NotificationController.SendRemiders | see contract | confirmed |
| BE-API-MCHANGO-016 | `POST /api/mobile/Notification/AddNotification` | `NotificationController.AddNotification` | NotificationController.AddNotification | see contract | confirmed |
| BE-API-MCHANGO-017 | `POST /api/mobile/Notification/GetAllNotification` | `NotificationController.GetAllNotification` | NotificationController.GetAllNotification | see contract | confirmed |
| BE-API-MCHANGO-018 | `POST /api/mobile/Notification/SendMchangoNotfication` | `NotificationController.SendMchangoNotfication` | NotificationController.SendMchangoNotfication | see contract | confirmed |
| BE-API-MCHANGO-019 | `POST /api/web/Encryption/encrypt` | `EncryptionController.EncryptAsync` | EncryptionController.EncryptAsync | see contract | confirmed |
| BE-API-MCHANGO-020 | `POST /api/web/Encryption/decrypt` | `EncryptionController.DecryptAsync` | EncryptionController.DecryptAsync | see contract | confirmed |
| BE-API-MCHANGO-021 | `POST /api/mobile/Transaction/InitiatePledgeTransaction` | `TransactionController.InitiatePledgeTransaction` | TransactionController.InitiatePledgeTransaction | see contract | confirmed |
| BE-API-MCHANGO-022 | `POST /api/mobile/Transaction/GetMyPledgeTransactions` | `TransactionController.GetMyPledgeTransactions` | TransactionController.GetMyPledgeTransactions | see contract | confirmed |
| BE-API-MCHANGO-023 | `POST /api/mobile/Transaction/GetMyContributions` | `TransactionController.GetMyContributions` | TransactionController.GetMyContributions | see contract | confirmed |
| BE-API-MCHANGO-024 | `POST /api/mobile/Transaction/GetMyTransactions` | `TransactionController.GetMyTransactions` | TransactionController.GetMyTransactions | see contract | confirmed |
| BE-API-MCHANGO-025 | `POST /api/mobile/Transaction/SendMoneyFeeCheck` | `TransactionController.SendMoneyFeeCheck` | TransactionController.SendMoneyFeeCheck | see contract | confirmed |
| BE-API-MCHANGO-026 | `POST /api/mobile/Transaction/SendMoneySubmit` | `TransactionController.SendMoneySubmit` | TransactionController.SendMoneySubmit | see contract | confirmed |
| BE-API-MCHANGO-027 | `POST /api/mobile/Transaction/LipaFeeCheck` | `TransactionController.LipaFeeCheck` | TransactionController.LipaFeeCheck | see contract | confirmed |
| BE-API-MCHANGO-028 | `POST /api/mobile/Transaction/LipaInitiateTransaction` | `TransactionController.LipaInitiateTransaction` | TransactionController.LipaInitiateTransaction | see contract | confirmed |
| BE-API-MCHANGO-029 | `POST /api/mobile/Transaction/MchangoFeeCheck` | `TransactionController.MchangoFeeCheck` | TransactionController.MchangoFeeCheck | see contract | confirmed |
| BE-API-MCHANGO-030 | `POST /api/mobile/Transaction/ContributeInitiateTransaction` | `TransactionController.MchangoInitiateTransaction` | TransactionController.MchangoInitiateTransaction | see contract | confirmed |
| BE-API-MCHANGO-031 | `POST /api/mobile/Transaction/CashoutPayment` | `TransactionController.CashoutPayment` | TransactionController.CashoutPayment | see contract | confirmed |
| BE-API-MCHANGO-032 | `POST /api/mobile/Transaction/CashoutFee` | `TransactionController.CashoutFee` | TransactionController.CashoutFee | see contract | confirmed |
| BE-API-MCHANGO-033 | `POST /api/mobile/Transaction/BankTransferFee` | `TransactionController.BankTransferFee` | TransactionController.BankTransferFee | see contract | confirmed |
| BE-API-MCHANGO-034 | `POST /api/mobile/Transaction/BankTransferPayment` | `TransactionController.BankTransferPayment` | TransactionController.BankTransferPayment | see contract | confirmed |
| BE-API-MCHANGO-035 | `POST /api/mobile/Transaction/MchangoCashoutFee` | `TransactionController.MchangoCashoutFee` | TransactionController.MchangoCashoutFee | see contract | confirmed |
| BE-API-MCHANGO-036 | `POST /api/mobile/MobileAppReports/GetMyReport` | `MobileAppReportsController.GetMyReport` | MobileAppReportsController.GetMyReport | see contract | confirmed |
| BE-API-MCHANGO-037 | `POST /api/mobile/Invitation/CreateEvent` | `InvitationController.CreateEvent` | InvitationController.CreateEvent | see contract | confirmed |
| BE-API-MCHANGO-038 | `POST /api/mobile/Invitation/UpdateEvent` | `InvitationController.UpdateEvent` | InvitationController.UpdateEvent | see contract | confirmed |
| BE-API-MCHANGO-039 | `POST /api/mobile/Invitation/GetEventById` | `InvitationController.GetEventById` | InvitationController.GetEventById | see contract | confirmed |
| BE-API-MCHANGO-040 | `POST /api/mobile/Invitation/GetAllEvents` | `InvitationController.GetAllEvents` | InvitationController.GetAllEvents | see contract | confirmed |
| BE-API-MCHANGO-041 | `POST /api/mobile/Invitation/DeleteEventById` | `InvitationController.DeleteEventById` | InvitationController.DeleteEventById | see contract | confirmed |
| BE-API-MCHANGO-042 | `POST /api/mobile/Invitation/CreateInvitation` | `InvitationController.CreateInvitation` | InvitationController.CreateInvitation | see contract | confirmed |
| BE-API-MCHANGO-043 | `POST /api/mobile/Invitation/ValidateInvitationCode` | `InvitationController.ValidateInvitationCode` | InvitationController.ValidateInvitationCode | see contract | confirmed |
| BE-API-MCHANGO-044 | `POST /api/mobile/Invitation/RedeemInvitationCode` | `InvitationController.RedeemInvitationCode` | InvitationController.RedeemInvitationCode | see contract | confirmed |
| BE-API-MCHANGO-045 | `POST /api/mobile/Invitation/GetAllInvitation` | `InvitationController.GetAllInvitation` | InvitationController.GetAllInvitation | see contract | confirmed |
| BE-API-MCHANGO-046 | `POST /api/mobile/Invitation/GetInvitationHistory` | `InvitationController.GetInvitationHistory` | InvitationController.GetInvitationHistory | see contract | confirmed |
| BE-API-MCHANGO-047 | `POST /api/mobile/SelfCare/CheckPinStatus` | `SelfCareController.CheckPinStatus` | SelfCareController.CheckPinStatus | see contract | confirmed |
| BE-API-MCHANGO-048 | `POST /api/mobile/SelfCare/ChangePIN` | `SelfCareController.ChangePIN` | SelfCareController.ChangePIN | see contract | confirmed |
| BE-API-MCHANGO-049 | `POST /api/mobile/Account/GetMyMchangoAccounts` | `AccountController.GetMyMchangoAccounts` | AccountController.GetMyMchangoAccounts | see contract | confirmed |
| BE-API-MCHANGO-050 | `POST /api/mobile/Account/GetMyMchangoAccountDetails` | `AccountController.GetMyMchangoAccountDetails` | AccountController.GetMyMchangoAccountDetails | see contract | confirmed |
| BE-API-MCHANGO-051 | `POST /api/mobile/Account/CreateAccount` | `AccountController.CreateAccount` | AccountController.CreateAccount | see contract | confirmed |
| BE-API-MCHANGO-052 | `POST /api/mobile/Account/CloseMchangoAccount` | `AccountController.CloseMchangoAccount` | AccountController.CloseMchangoAccount | see contract | confirmed |
| BE-API-MCHANGO-053 | `POST /api/mobile/Account/ChangeAccountRole` | `AccountController.ChangeAccountRole` | AccountController.ChangeAccountRole | see contract | confirmed |
| BE-API-MCHANGO-054 | `POST /api/mobile/Account/CreateAccountRole` | `AccountController.CreateAccountRole` | AccountController.CreateAccountRole | see contract | confirmed |
| BE-API-MCHANGO-055 | `POST /api/mobile/Account/GetAllRoleByAccount` | `AccountController.GetAllRoleByAccount` | AccountController.GetAllRoleByAccount | see contract | confirmed |
| BE-API-MCHANGO-056 | `POST /api/mobile/Account/DeleteAccountRole` | `AccountController.DeleteAccountRole` | AccountController.DeleteAccountRole | see contract | confirmed |
| BE-API-MCHANGO-057 | `POST /api/mobile/Account/GetMyMchangoAccountPurposeAndDuration` | `AccountController.GetMyMchangoAccountPurposeAndDuration` | AccountController.GetMyMchangoAccountPurposeAndDuration | see contract | confirmed |
| BE-API-MCHANGO-058 | `GET /api/web/AccountReports/GetMyMchangoAccountReport` | `AccountReportsController.GetMyMchangoAccountReport` | AccountReportsController.GetMyMchangoAccountReport | see contract | confirmed |
| BE-API-MCHANGO-059 | `GET /api/web/AccountReports/GetGroupBalanceReport` | `AccountReportsController.GetGroupBalanceReport` | AccountReportsController.GetGroupBalanceReport | see contract | confirmed |
| BE-API-MCHANGO-060 | `GET /api/web/AccountReports/GetMyMchangoAccountStatementReport` | `AccountReportsController.GetMyMchangoAccountStatementReport` | AccountReportsController.GetMyMchangoAccountStatementReport | see contract | confirmed |
| BE-API-MCHANGO-061 | `POST /api/web/Auth/login` | `AuthController.LoginAsync` | AuthController.LoginAsync | see contract | confirmed |
| BE-API-MCHANGO-062 | `POST /api/web/Account/GetAllActiveAccounts` | `AccountController.GetMyMchangoAccounts` | AccountController.GetMyMchangoAccounts | see contract | confirmed |
| BE-API-MCHANGO-063 | `POST /api/web/Account/ChangeAccountPaymentStatus` | `AccountController.ChangeAccountPaymentStatus` | AccountController.ChangeAccountPaymentStatus | see contract | confirmed |
| BE-API-MCHANGO-064 | `POST /api/web/Account/SendMchangoNotfication` | `AccountController.SendMchangoNotfication` | AccountController.SendMchangoNotfication | see contract | confirmed |

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
| `T` / `Table` | EF set |
| `T` / `_entities` | EF set |
| `T` / `Entities` | EF set |
| `T` / `Table` | EF set |
| `mchangoqrconfiguration` / `mchangoqrconfiguration` | EF set |
| `mchangoaccountconfiguration` / `mchangoaccountconfiguration` | EF set |
| `mchangointerestconfiguration` / `mchangointerestconfiguration` | EF set |
| `AccountEntityModel` / `Accounts` | EF set |
| `PurposeEntityModel` / `Purposes` | EF set |
| `PledgeTransactionEntityModel` / `PledgeTransactions` | EF set |
| `ActualTransactionEntityModel` / `ActualTransactions` | EF set |
| `RoleEntityModel` / `Roles` | EF set |
| `NotificationEntityModel` / `Notifications` | EF set |
| `EventEntityModel` / `Events` | EF set |
| `InvitationEntityModel` / `Invitations` | EF set |
| `PoolAccountEntityModel` / `PoolAccounts` | EF set |
| `AccountRoleEntityModel` / `AccountRoles` | EF set |
| `AccountDurationTypeEntityModel` / `AccountDurationTypes` | EF set |
| `MchangoTransactionHistoryEntityModel` / `MchangoTransactionHistories` | EF set |
| `BankTransactionHistoryEntityModel` / `BankTransactionHistories` | EF set |
| `CashoutTransactionHistoryEntityModel` / `CashoutTransactionHistories` | EF set |
| `AccountInterestCalculationEntityModel` / `AccountInterestCalculations` | EF set |
| `GrossInterestCalculationEntityModel` / `GrossInterestCalculations` | EF set |
| `AddNotificationEntityModel` / `AddNotifications` | EF set |
| `TransactionHistoryEntityModel` / `TransactionHistory` | EF set |
| `MChangoReportRequestsEntityModel` / `MChangoReportRequests` | EF set |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`BankTransferFee`, `BankTransferPayment`, `CashOutPayment`, `CashoutFee`, `ChangeGroupURL`, `ConfigAPIUrl`, `CorsOrigins:AllowedOrigins`, `CreateAccountURL`, `EmailCC`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `EnableLog:Warning`, `EncryptionSecret (key name)<redacted-purpose>`, `Encryption_Decryption_Key`, `External2TelepinGenericEndpoint:<redacted-purpose>`, `External2TelepinGenericEndpoint:EndpointUrl`, `External2TelepinGenericEndpoint:TerminalType`, `External2TelepinGenericEndpoint:UserName`, `FCMNotify`, `GetBalance`, `GetUserDetailURL`, `IV`, `IsRedisCluster`, `LoginURL`, `MchangoCashoutFee`, `OTPSource`, `Origins`, `Partner:ApiBaseUrl`, `Partner:XAuthKey`, `RTT_EmailTo`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:LogURL`, `RabbitMQ:QueueName`, `RabbitMQ:Username`, `RedisPassword (key name)<redacted-purpose>`, `RedisURL`, `SendFCMViaService`, `SendMoneyFee`, `SendMoneyPayment`

## Open questions
- Gateway public URLs not in-repo.
