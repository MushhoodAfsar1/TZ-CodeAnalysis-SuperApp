---
kb_section: backend
type: service
ids: [BE-SVC-MERCH]
service: MERCH
repo: TZ-Tigo-SuperApp-Merchant
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 2367767
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-MERCH TZ-Tigo-SuperApp-Merchant
**Repo:** `TZ-Tigo-SuperApp-Merchant` · **Type:** service · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `2367767`
**Purpose:** Merchant

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-MERCH-001 | POST /api/Settlement/GetTransferScheduleById | SettlementController.GetTransferScheduleById | — | none | confirmed |
| BE-API-MERCH-002 | POST /api/Settlement/GetTransferScheduleByMSISDN | SettlementController.GetTransferScheduleByMSISDN | — | none | confirmed |
| BE-API-MERCH-003 | POST /api/Settlement | SettlementController.GetAllTransferSchedules | — | none | confirmed |
| BE-API-MERCH-004 | POST /api/Settlement/GetActiveTransferSchedule | SettlementController.GetActiveTransferSchedules | — | none | confirmed |
| BE-API-MERCH-005 | POST /api/Settlement/AcceptTermsandCondition | SettlementController.AddSettlementTc | — | none | confirmed |
| BE-API-MERCH-006 | POST /api/Settlement/ListSettlement | SettlementController.ListSettlement | — | none | confirmed |
| BE-API-MERCH-007 | POST /api/Settlement/importcsv | SettlementController.ImportBundles | — | none | confirmed |
| BE-API-MERCH-008 | POST /api/Settlement/enc | SettlementController.enc | — | none | confirmed |
| BE-API-MERCH-009 | POST /api/Settlement/dec | SettlementController.dec | — | none | confirmed |
| BE-API-MERCH-010 | POST /api/Merchant | MerchantController.RegisterDevice | — | none | confirmed |
| BE-API-MERCH-011 | POST /api/Merchant | MerchantController.VerifyDevice | — | none | confirmed |
| BE-API-MERCH-012 | POST /api/Merchant | MerchantController.GetSessionToken | — | none | confirmed |
| BE-API-MERCH-013 | POST /api/Merchant | MerchantController.GenerateQR | — | none | confirmed |
| BE-API-MERCH-014 | POST /api/Merchant | MerchantController.MerchantLookup | — | none | confirmed |
| BE-API-MERCH-015 | POST /api/Merchant | MerchantController.ListEntityUsers | — | none | confirmed |
| BE-API-MERCH-016 | POST /api/Merchant | MerchantController.ModifyEntityUser | — | none | confirmed |
| BE-API-MERCH-017 | POST /api/Merchant | MerchantController.CreateEntityUser | — | none | confirmed |
| BE-API-MERCH-018 | POST /api/Merchant | MerchantController.IsPINReset | — | none | confirmed |
| BE-API-MERCH-019 | POST /api/Merchant | MerchantController.ChangeMerchantPin | — | none | confirmed |
| BE-API-MERCH-020 | POST /api/Merchant | MerchantController.TransactionHistory | — | none | confirmed |
| BE-API-MERCH-021 | POST /api/Merchant | MerchantController.PerformanceAnalytics | — | none | confirmed |
| BE-API-MERCH-022 | POST /api/Merchant/dec | MerchantController.dec | — | none | confirmed |
| BE-API-MERCH-023 | POST /api/Merchant/encRegisterDevice | MerchantController.encRegisterDevice | — | none | confirmed |
| BE-API-MERCH-024 | POST /api/Merchant/encVerifyDevice | MerchantController.encVerifyDevice | — | none | confirmed |
| BE-API-MERCH-025 | POST /api/Merchant/encGetSessionToken | MerchantController.encGetSessionToken | — | none | confirmed |
| BE-API-MERCH-026 | POST /api/Merchant/encGenerateQR | MerchantController.encGenerateQR | — | none | confirmed |
| BE-API-MERCH-027 | POST /api/Merchant/encUpdateMerchantStatus | MerchantController.encUpdateMerchantStatus | — | none | confirmed |
| BE-API-MERCH-028 | POST /api/Merchant/encIsPinReset | MerchantController.encIsPinReset | — | none | confirmed |
| BE-API-MERCH-029 | POST /api/Notification | NotificationController.Notification | — | none | confirmed |
| BE-API-MERCH-030 | POST /api/Notification | NotificationController.GetEntityDetail | — | none | confirmed |
| BE-API-MERCH-031 | POST /api/Notification/enc | NotificationController.enc | — | none | confirmed |
| BE-API-MERCH-032 | POST /api/RequestToPay | RequestToPayController.CreatePaymentRequest | — | none | confirmed |
| BE-API-MERCH-033 | POST /api/RequestToPay | RequestToPayController.VerifySendMoney | — | none | confirmed |
| BE-API-MERCH-034 | POST /api/RequestToPay | RequestToPayController.TransferSendMoney | — | none | confirmed |
| BE-API-MERCH-035 | POST /api/RequestToPay | RequestToPayController.BillerCallback | — | none | confirmed |
| BE-API-MERCH-036 | POST /api/RequestToPay | RequestToPayController.GetDashboardData | — | none | confirmed |
| BE-API-MERCH-037 | POST /api/RequestToPay | RequestToPayController.GetConsumerActiveRequests | — | none | confirmed |
| BE-API-MERCH-038 | POST /api/RequestToPay | RequestToPayController.UpdateRequestStatus | — | none | confirmed |
| BE-API-MERCH-039 | POST /api/DynamicQR | DynamicQRController.GenerateQR | — | none | confirmed |
| BE-API-MERCH-040 | POST /api/Schedular/AddEditSchedule | SchedularController.AddEditSchedule | — | none | confirmed |
| BE-API-MERCH-041 | POST /api/Schedular/ChangeScheduleStatus | SchedularController.ChangeScheduleStatus | — | none | confirmed |
| BE-API-MERCH-042 | POST /api/Schedular/MerchantLinkAccount | SchedularController.MerchantLinkAccount | — | none | confirmed |
| BE-API-MERCH-043 | POST /api/Schedular/enc | SchedularController.enc | — | none | confirmed |
| BE-API-MERCH-044 | POST /api/Schedular/dec | SchedularController.dec | — | none | confirmed |
| BE-API-MERCH-045 | POST /api/MerchantCashout | MerchantCashoutController.CashoutFee | — | none | confirmed |
| BE-API-MERCH-046 | POST /api/MerchantCashout | MerchantCashoutController.CashOut | — | none | confirmed |


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
