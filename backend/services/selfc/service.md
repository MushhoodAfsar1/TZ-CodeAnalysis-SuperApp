---
kb_section: backend
type: service
ids: [BE-SVC-SELFC]
service: SELFC
repo: TZ-Tigo-SuperApp-SelfCare
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: a0aeca8
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-SELFC Self-care (block, SMS, conversion)
**Repo:** `TZ-Tigo-SuperApp-SelfCare` · **Type:** service · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `a0aeca8`
**Purpose:** Self-care (block, SMS, conversion)

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, RabbitMQ.Client, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-SELFC-001 | `POST /api/UnsolicitedSMS` | `UnsolicitedSMSController.UnsolicitedSMS` | UnsolicitedSMSController.UnsolicitedSMS | see contract | confirmed |
| BE-API-SELFC-002 | `POST /api/UnsolicitedSMS/SaveSMS` | `UnsolicitedSMSController.SaveSMS` | UnsolicitedSMSController.SaveSMS | see contract | confirmed |
| BE-API-SELFC-003 | `POST /api/UnsolicitedSMS/SMSInsights` | `UnsolicitedSMSController.SMSInsights` | UnsolicitedSMSController.SMSInsights | see contract | confirmed |
| BE-API-SELFC-004 | `POST /api/UnsolicitedSMS/GetUserPreference` | `UnsolicitedSMSController.GetUserPreference` | UnsolicitedSMSController.GetUserPreference | see contract | confirmed |
| BE-API-SELFC-005 | `POST /api/SelfCare/UnblockAccount` | `SelfCareController.UnblockAccount` | SelfCareController.UnblockAccount | see contract | confirmed |
| BE-API-SELFC-006 | `POST /api/SelfCare/TransactionHistory` | `SelfCareController.TransactionHistory` | SelfCareController.TransactionHistory | see contract | confirmed |
| BE-API-SELFC-007 | `POST /api/SelfCare/PinResetStatus` | `SelfCareController.PinResetStatus` | SelfCareController.PinResetStatus | see contract | confirmed |
| BE-API-SELFC-008 | `POST /api/SelfCare/CheckPinStatus` | `SelfCareController.CheckPinStatus` | SelfCareController.CheckPinStatus | see contract | confirmed |
| BE-API-SELFC-009 | `POST /api/SelfCare/PinReset` | `SelfCareController.PinReset` | SelfCareController.PinReset | see contract | confirmed |
| BE-API-SELFC-010 | `POST /api/SelfCare/ChangePIN` | `SelfCareController.ChangePIN` | SelfCareController.ChangePIN | see contract | confirmed |
| BE-API-SELFC-011 | `POST /api/SelfCare/CancelPINReset` | `SelfCareController.CancelPINReset` | SelfCareController.CancelPINReset | see contract | confirmed |
| BE-API-SELFC-012 | `POST /api/SelfCare/GetMonthlyStatement` | `SelfCareController.GetMonthlyStatement` | SelfCareController.GetMonthlyStatement | see contract | confirmed |
| BE-API-SELFC-013 | `POST /api/SelfCare/TransactionHistoryDetail` | `SelfCareController.TransactionHistoryDetail` | SelfCareController.TransactionHistoryDetail | see contract | confirmed |
| BE-API-SELFC-014 | `POST /api/SelfCare/FetchTransactions` | `SelfCareController.FetchTransactions` | SelfCareController.FetchTransactions | see contract | confirmed |
| BE-API-SELFC-015 | `POST /api/SelfCare/InitiateReversal` | `SelfCareController.InitiateReversal` | SelfCareController.InitiateReversal | see contract | confirmed |
| BE-API-SELFC-016 | `POST /api/SelfCare/PartialReversal` | `SelfCareController.PartialReversal` | SelfCareController.PartialReversal | see contract | confirmed |
| BE-API-SELFC-017 | `POST /api/SelfCare/FetchPendingApproval` | `SelfCareController.FetchPendingApproval` | SelfCareController.FetchPendingApproval | see contract | confirmed |
| BE-API-SELFC-018 | `POST /api/SelfCare/ReversalApprove` | `SelfCareController.ReversalApprove` | SelfCareController.ReversalApprove | see contract | confirmed |
| BE-API-SELFC-019 | `POST /api/SelfCare/MyNumber` | `SelfCareController.MyNumber` | SelfCareController.MyNumber | see contract | confirmed |
| BE-API-SELFC-020 | `POST /api/SelfCare/GetMerchantInfo` | `SelfCareController.GetMerchantInfo` | SelfCareController.GetMerchantInfo | see contract | confirmed |
| BE-API-SELFC-021 | `POST /api/SelfCare/MyNumberAndMerchantInfo` | `SelfCareController.MyNumberAndMerchantInfo` | SelfCareController.MyNumberAndMerchantInfo | see contract | confirmed |
| BE-API-SELFC-022 | `POST /api/SelfCare/RegistrationDetail` | `SelfCareController.RegistrationDetail` | SelfCareController.RegistrationDetail | see contract | confirmed |
| BE-API-SELFC-023 | `POST /api/SelfCare/GetLukuTransactions` | `SelfCareController.GetLukuTransactions` | SelfCareController.GetLukuTransactions | see contract | confirmed |
| BE-API-SELFC-024 | `POST /api/SelfCare/GetLukuTokens` | `SelfCareController.GetLukuTokens` | SelfCareController.GetLukuTokens | see contract | confirmed |
| BE-API-SELFC-025 | `POST /api/SelfCare/GetTransactionDetails` | `SelfCareController.GetTransactionDetails` | SelfCareController.GetTransactionDetails | see contract | confirmed |
| BE-API-SELFC-026 | `POST /api/SelfCare/enc` | `SelfCareController.enc` | SelfCareController.enc | see contract | confirmed |
| BE-API-SELFC-027 | `POST /api/SelfCare/MyNumberOtp` | `SelfCareController.mMyNumberOTP` | SelfCareController.mMyNumberOTP | see contract | confirmed |
| BE-API-SELFC-028 | `POST /api/SelfCare/MyNumberOtpVerify` | `SelfCareController.MyNumberOtpVerify` | SelfCareController.MyNumberOtpVerify | see contract | confirmed |
| BE-API-SELFC-029 | `POST /api/SelfCare/DeleteMyNumber` | `SelfCareController.DeleteMyNumber` | SelfCareController.DeleteMyNumber | see contract | confirmed |
| BE-API-SELFC-030 | `POST /api/SelfCare/TukuzaTransactions` | `SelfCareController.TukuzaTransactions` | SelfCareController.TukuzaTransactions | see contract | confirmed |
| BE-API-SELFC-031 | `POST /api/SelfCare/TukuzaToken` | `SelfCareController.TukuzaToken` | SelfCareController.TukuzaToken | see contract | confirmed |
| BE-API-SELFC-032 | `POST /api/SelfCare/GenerateQR` | `SelfCareController.GenerateQR` | SelfCareController.GenerateQR | see contract | confirmed |
| BE-API-SELFC-033 | `POST /api/SelfCare/FraudDetection` | `SelfCareController.FraudDetection` | SelfCareController.FraudDetection | see contract | confirmed |
| BE-API-SELFC-034 | `POST /api/SelfCare/TransactionHistoryDetailV1` | `SelfCareController.TransactionHistoryDetailV1` | SelfCareController.TransactionHistoryDetailV1 | see contract | confirmed |
| BE-API-SELFC-035 | `POST /api/SelfCare/GetMonthlyStatementV1` | `SelfCareController.GetMonthlyStatementV1` | SelfCareController.GetMonthlyStatementV1 | see contract | confirmed |
| BE-API-SELFC-036 | `POST /api/Conversion/encUnblockAccount` | `ConversionController.encUnblockAccount` | ConversionController.encUnblockAccount | see contract | confirmed |
| BE-API-SELFC-037 | `POST /api/Conversion/encTransactionHistory` | `ConversionController.encTransactionHistory` | ConversionController.encTransactionHistory | see contract | confirmed |
| BE-API-SELFC-038 | `POST /api/Conversion/encPinResetStatus` | `ConversionController.encPinResetStatus` | ConversionController.encPinResetStatus | see contract | confirmed |
| BE-API-SELFC-039 | `POST /api/Conversion/encPinReset` | `ConversionController.encPinReset` | ConversionController.encPinReset | see contract | confirmed |
| BE-API-SELFC-040 | `POST /api/Conversion/encCancelPINReset` | `ConversionController.encCancelPINReset` | ConversionController.encCancelPINReset | see contract | confirmed |
| BE-API-SELFC-041 | `POST /api/Conversion/encGetMonthlyStatement` | `ConversionController.encGetMonthlyStatement` | ConversionController.encGetMonthlyStatement | see contract | confirmed |
| BE-API-SELFC-042 | `POST /api/Conversion/encInitiateReversal` | `ConversionController.encInitiateReversal` | ConversionController.encInitiateReversal | see contract | confirmed |
| BE-API-SELFC-043 | `POST /api/Conversion/encPartialReversal` | `ConversionController.encPartialReversal` | ConversionController.encPartialReversal | see contract | confirmed |
| BE-API-SELFC-044 | `POST /api/Conversion/encFetchPendingApproval` | `ConversionController.encFetchPendingApproval` | ConversionController.encFetchPendingApproval | see contract | confirmed |
| BE-API-SELFC-045 | `POST /api/Conversion/encReversalApprove` | `ConversionController.encReversalApprove` | ConversionController.encReversalApprove | see contract | confirmed |
| BE-API-SELFC-046 | `POST /api/Conversion/encMyNumber` | `ConversionController.encMyNumber` | ConversionController.encMyNumber | see contract | confirmed |
| BE-API-SELFC-047 | `POST /api/Conversion/encChangePIN` | `ConversionController.encChangePIN` | ConversionController.encChangePIN | see contract | confirmed |
| BE-API-SELFC-048 | `POST /api/Conversion/encRegistrationDetail` | `ConversionController.encRegistrationDetail` | ConversionController.encRegistrationDetail | see contract | confirmed |
| BE-API-SELFC-049 | `POST /api/Conversion/encFetchTransactions` | `ConversionController.encRegistrationDetail` | ConversionController.encRegistrationDetail | see contract | confirmed |
| BE-API-SELFC-050 | `POST /api/Conversion/encMyNumberandMerchantInfo` | `ConversionController.encMyNumberandMerchantInfo` | ConversionController.encMyNumberandMerchantInfo | see contract | confirmed |
| BE-API-SELFC-051 | `POST /api/Conversion/encLukuToken` | `ConversionController.encLukuToken` | ConversionController.encLukuToken | see contract | confirmed |
| BE-API-SELFC-052 | `POST /api/Conversion/decrypt` | `ConversionController.Decrypt` | ConversionController.Decrypt | see contract | confirmed |
| BE-API-SELFC-053 | `POST /api/BlockNumber/NidaValidation` | `BlockNumberController.NidaValidation` | BlockNumberController.NidaValidation | see contract | confirmed |
| BE-API-SELFC-054 | `POST /api/BlockNumber/BlockMyNumber` | `BlockNumberController.BlockMyNumber` | BlockNumberController.BlockMyNumber | see contract | confirmed |
| BE-API-SELFC-055 | `POST /api/BlockNumber/BlockMyNumberRequest` | `BlockNumberController.encNidaValidation` | BlockNumberController.encNidaValidation | see contract | confirmed |
| BE-API-SELFC-056 | `POST /api/BlockNumber/encrypt` | `BlockNumberController.Encrypt` | BlockNumberController.Encrypt | see contract | confirmed |
| BE-API-SELFC-057 | `POST /api/BlockNumber/decrypt` | `BlockNumberController.Decrypt` | BlockNumberController.Decrypt | see contract | confirmed |

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
| `MerchantQRConfiguration` / `merchantqrconfiguration` | EF set |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`AzureBlobStorage:<redacted-purpose>`, `AzureBlobStorage:DashboardContainer`, `AzureBlobStorage:DiasporaContainer`, `BaseAuthorization`, `BlockNumberAPI`, `CallBackSuperAppLUKUQueryTokenSync`, `CancelPINReset`, `CheckMFSStatus`, `CheckPINStatus`, `ClaimMissing`, `ConfigAPIUrl`, `DBServerUrl`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `Encryption_Decryption_Key`, `FCMNotify`, `FraudDetection:Authorization`, `FraudDetection:URL`, `IV`, `IsRedisCluster`, `MFSAccountType`, `MiniStatement`, `NidaValidation`, `OTPSource`, `OtpExpiryInSec`, `OtpLength`, `PinValidation`, `RTSTransactionHistory:TransactionHistoryURL`, `RTSTransactionHistory:api-key`, `RTSTransactionHistory:user-id`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:LogQueueName`, `RabbitMQ:LogURL`, `RabbitMQ:QueueName`, `RabbitMQ:Username`, `RedisPassword (key name)<redacted-purpose>`, `RedisURL`, `SMSConfig:MaxPromptsPerDay`, `SMSConfig:MaxPromptsPerMonth`

## Open questions
- Gateway public URLs not in-repo.
