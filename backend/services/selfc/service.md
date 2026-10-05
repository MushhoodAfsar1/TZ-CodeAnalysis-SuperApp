---
kb_section: backend
type: service
ids: [BE-SVC-SELFC]
service: SELFC
repo: TZ-Tigo-SuperApp-SelfCare
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: a0aeca8
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-SELFC TZ-Tigo-SuperApp-SelfCare
**Repo:** `TZ-Tigo-SuperApp-SelfCare` · **Type:** service · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `a0aeca8`
**Purpose:** Self-care

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-SELFC-001 | POST /api/SelfCare | SelfCareController.UnblockAccount | — | none | confirmed |
| BE-API-SELFC-002 | POST /api/SelfCare | SelfCareController.TransactionHistory | — | none | confirmed |
| BE-API-SELFC-003 | POST /api/SelfCare | SelfCareController.PinResetStatus | — | none | confirmed |
| BE-API-SELFC-004 | POST /api/SelfCare | SelfCareController.CheckPinStatus | — | none | confirmed |
| BE-API-SELFC-005 | POST /api/SelfCare | SelfCareController.PinReset | — | none | confirmed |
| BE-API-SELFC-006 | POST /api/SelfCare | SelfCareController.ChangePIN | — | none | confirmed |
| BE-API-SELFC-007 | POST /api/SelfCare | SelfCareController.CancelPINReset | — | none | confirmed |
| BE-API-SELFC-008 | POST /api/SelfCare | SelfCareController.GetMonthlyStatement | — | none | confirmed |
| BE-API-SELFC-009 | POST /api/SelfCare | SelfCareController.TransactionHistoryDetail | — | none | confirmed |
| BE-API-SELFC-010 | POST /api/SelfCare | SelfCareController.FetchTransactions | — | none | confirmed |
| BE-API-SELFC-011 | POST /api/SelfCare | SelfCareController.InitiateReversal | — | none | confirmed |
| BE-API-SELFC-012 | POST /api/SelfCare | SelfCareController.PartialReversal | — | none | confirmed |
| BE-API-SELFC-013 | POST /api/SelfCare | SelfCareController.FetchPendingApproval | — | none | confirmed |
| BE-API-SELFC-014 | POST /api/SelfCare | SelfCareController.ReversalApprove | — | none | confirmed |
| BE-API-SELFC-015 | POST /api/SelfCare | SelfCareController.MyNumber | — | none | confirmed |
| BE-API-SELFC-016 | POST /api/SelfCare | SelfCareController.GetMerchantInfo | — | none | confirmed |
| BE-API-SELFC-017 | POST /api/SelfCare | SelfCareController.MyNumberAndMerchantInfo | — | none | confirmed |
| BE-API-SELFC-018 | POST /api/SelfCare | SelfCareController.RegistrationDetail | — | none | confirmed |
| BE-API-SELFC-019 | POST /api/SelfCare | SelfCareController.GetLukuTransactions | — | none | confirmed |
| BE-API-SELFC-020 | POST /api/SelfCare | SelfCareController.GetLukuTokens | — | none | confirmed |
| BE-API-SELFC-021 | POST /api/SelfCare | SelfCareController.GetTransactionDetails | — | none | confirmed |
| BE-API-SELFC-022 | POST /api/SelfCare/enc | SelfCareController.enc | — | none | confirmed |
| BE-API-SELFC-023 | POST /api/SelfCare | SelfCareController.mMyNumberOTP | — | none | confirmed |
| BE-API-SELFC-024 | POST /api/SelfCare | SelfCareController.MyNumberOtpVerify | — | none | confirmed |
| BE-API-SELFC-025 | POST /api/SelfCare | SelfCareController.DeleteMyNumber | — | none | confirmed |
| BE-API-SELFC-026 | POST /api/SelfCare | SelfCareController.TukuzaTransactions | — | none | confirmed |
| BE-API-SELFC-027 | POST /api/SelfCare | SelfCareController.TukuzaToken | — | none | confirmed |
| BE-API-SELFC-028 | POST /api/SelfCare | SelfCareController.GenerateQR | — | none | confirmed |
| BE-API-SELFC-029 | POST /api/SelfCare | SelfCareController.FraudDetection | — | none | confirmed |
| BE-API-SELFC-030 | POST /api/SelfCare | SelfCareController.TransactionHistoryDetailV1 | — | none | confirmed |
| BE-API-SELFC-031 | POST /api/SelfCare | SelfCareController.GetMonthlyStatementV1 | — | none | confirmed |
| BE-API-SELFC-032 | POST /api/BlockNumber | BlockNumberController.NidaValidation | — | none | confirmed |
| BE-API-SELFC-033 | POST /api/BlockNumber | BlockNumberController.BlockMyNumber | — | none | confirmed |
| BE-API-SELFC-034 | POST /api/BlockNumber/BlockMyNumberRequest | BlockNumberController.encNidaValidation | — | none | confirmed |
| BE-API-SELFC-035 | POST /api/BlockNumber/encrypt | BlockNumberController.Encrypt | — | none | confirmed |
| BE-API-SELFC-036 | POST /api/BlockNumber/decrypt | BlockNumberController.Decrypt | — | none | confirmed |
| BE-API-SELFC-037 | POST /api | UnsolicitedSMSController.UnsolicitedSMS | — | none | confirmed |
| BE-API-SELFC-038 | POST /api | UnsolicitedSMSController.SaveSMS | — | none | confirmed |
| BE-API-SELFC-039 | POST /api | UnsolicitedSMSController.SMSInsights | — | none | confirmed |
| BE-API-SELFC-040 | POST /api | UnsolicitedSMSController.GetUserPreference | — | none | confirmed |
| BE-API-SELFC-041 | POST /api/Conversion/encUnblockAccount | ConversionController.encUnblockAccount | — | none | confirmed |
| BE-API-SELFC-042 | POST /api/Conversion/encTransactionHistory | ConversionController.encTransactionHistory | — | none | confirmed |
| BE-API-SELFC-043 | POST /api/Conversion/encPinResetStatus | ConversionController.encPinResetStatus | — | none | confirmed |
| BE-API-SELFC-044 | POST /api/Conversion/encPinReset | ConversionController.encPinReset | — | none | confirmed |
| BE-API-SELFC-045 | POST /api/Conversion/encCancelPINReset | ConversionController.encCancelPINReset | — | none | confirmed |
| BE-API-SELFC-046 | POST /api/Conversion/encGetMonthlyStatement | ConversionController.encGetMonthlyStatement | — | none | confirmed |
| BE-API-SELFC-047 | POST /api/Conversion/encInitiateReversal | ConversionController.encInitiateReversal | — | none | confirmed |
| BE-API-SELFC-048 | POST /api/Conversion/encPartialReversal | ConversionController.encPartialReversal | — | none | confirmed |
| BE-API-SELFC-049 | POST /api/Conversion/encFetchPendingApproval | ConversionController.encFetchPendingApproval | — | none | confirmed |
| BE-API-SELFC-050 | POST /api/Conversion/encReversalApprove | ConversionController.encReversalApprove | — | none | confirmed |
| BE-API-SELFC-051 | POST /api/Conversion/encMyNumber | ConversionController.encMyNumber | — | none | confirmed |
| BE-API-SELFC-052 | POST /api/Conversion/encChangePIN | ConversionController.encChangePIN | — | none | confirmed |
| BE-API-SELFC-053 | POST /api/Conversion/encRegistrationDetail | ConversionController.encRegistrationDetail | — | none | confirmed |
| BE-API-SELFC-054 | POST /api/Conversion/encFetchTransactions | ConversionController.encRegistrationDetail | — | none | confirmed |
| BE-API-SELFC-055 | POST /api/Conversion/encMyNumberandMerchantInfo | ConversionController.encMyNumberandMerchantInfo | — | none | confirmed |
| BE-API-SELFC-056 | POST /api/Conversion/encLukuToken | ConversionController.encLukuToken | — | none | confirmed |
| BE-API-SELFC-057 | POST /api/Conversion/decrypt | ConversionController.Decrypt | — | none | confirmed |


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
