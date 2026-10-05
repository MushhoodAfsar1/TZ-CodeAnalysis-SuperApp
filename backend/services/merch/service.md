---
kb_section: backend
type: service
ids: [BE-SVC-MERCH]
service: MERCH
repo: TZ-Tigo-SuperApp-Merchant
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 2367767
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-MERCH Merchant QR, RTP, cash-out, settlement schedules
**Repo:** `TZ-Tigo-SuperApp-Merchant` · **Type:** service · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `2367767`
**Purpose:** Merchant QR, RTP, cash-out, settlement schedules

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, RabbitMQ.Client, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-MERCH-001 | `POST /api/MerchantCashout/CashoutFee` | `MerchantCashoutController.CashoutFee` | MerchantCashoutController.CashoutFee | see contract | confirmed |
| BE-API-MERCH-002 | `POST /api/MerchantCashout/CashoutPayment` | `MerchantCashoutController.CashOut` | MerchantCashoutController.CashOut | see contract | confirmed |
| BE-API-MERCH-003 | `POST /api/Notification/Notification` | `NotificationController.Notification` | NotificationController.Notification | see contract | confirmed |
| BE-API-MERCH-004 | `POST /api/Notification/GetEntityDetail` | `NotificationController.GetEntityDetail` | NotificationController.GetEntityDetail | see contract | confirmed |
| BE-API-MERCH-005 | `POST /api/Notification/enc` | `NotificationController.enc` | NotificationController.enc | see contract | confirmed |
| BE-API-MERCH-006 | `POST /api/Schedular/AddEditSchedule` | `SchedularController.AddEditSchedule` | SchedularController.AddEditSchedule | see contract | confirmed |
| BE-API-MERCH-007 | `POST /api/Schedular/ChangeScheduleStatus` | `SchedularController.ChangeScheduleStatus` | SchedularController.ChangeScheduleStatus | see contract | confirmed |
| BE-API-MERCH-008 | `POST /api/Schedular/MerchantLinkAccount` | `SchedularController.MerchantLinkAccount` | SchedularController.MerchantLinkAccount | see contract | confirmed |
| BE-API-MERCH-009 | `POST /api/Schedular/enc` | `SchedularController.enc` | SchedularController.enc | see contract | confirmed |
| BE-API-MERCH-010 | `POST /api/Schedular/dec` | `SchedularController.dec` | SchedularController.dec | see contract | partial |
| BE-API-MERCH-011 | `POST /api/RequestToPay/CreatePaymentRequest` | `RequestToPayController.CreatePaymentRequest` | RequestToPayController.CreatePaymentRequest | see contract | confirmed |
| BE-API-MERCH-012 | `POST /api/RequestToPay/VerifySendMoney` | `RequestToPayController.VerifySendMoney` | RequestToPayController.VerifySendMoney | see contract | confirmed |
| BE-API-MERCH-013 | `POST /api/RequestToPay/TransferSendMoney` | `RequestToPayController.TransferSendMoney` | RequestToPayController.TransferSendMoney | see contract | confirmed |
| BE-API-MERCH-014 | `POST /api/RequestToPay/BillerCallback` | `RequestToPayController.BillerCallback` | RequestToPayController.BillerCallback | see contract | confirmed |
| BE-API-MERCH-015 | `POST /api/RequestToPay/GetDashboardData` | `RequestToPayController.GetDashboardData` | RequestToPayController.GetDashboardData | see contract | confirmed |
| BE-API-MERCH-016 | `POST /api/RequestToPay/GetConsumerActiveRequests` | `RequestToPayController.GetConsumerActiveRequests` | RequestToPayController.GetConsumerActiveRequests | see contract | confirmed |
| BE-API-MERCH-017 | `POST /api/RequestToPay/UpdateRequestStatus` | `RequestToPayController.UpdateRequestStatus` | RequestToPayController.UpdateRequestStatus | see contract | confirmed |
| BE-API-MERCH-018 | `POST /api/Merchant/RegisterDevice` | `MerchantController.RegisterDevice` | MerchantController.RegisterDevice | see contract | confirmed |
| BE-API-MERCH-019 | `POST /api/Merchant/VerifyDevice` | `MerchantController.VerifyDevice` | MerchantController.VerifyDevice | see contract | confirmed |
| BE-API-MERCH-020 | `POST /api/Merchant/GetSessionToken` | `MerchantController.GetSessionToken` | MerchantController.GetSessionToken | see contract | confirmed |
| BE-API-MERCH-021 | `POST /api/Merchant/GenerateQR` | `MerchantController.GenerateQR` | MerchantController.GenerateQR | see contract | confirmed |
| BE-API-MERCH-022 | `POST /api/Merchant/MerchantLookup` | `MerchantController.MerchantLookup` | MerchantController.MerchantLookup | see contract | confirmed |
| BE-API-MERCH-023 | `POST /api/Merchant/ListEntityUsers` | `MerchantController.ListEntityUsers` | MerchantController.ListEntityUsers | see contract | confirmed |
| BE-API-MERCH-024 | `POST /api/Merchant/ModifyEntityUser` | `MerchantController.ModifyEntityUser` | MerchantController.ModifyEntityUser | see contract | confirmed |
| BE-API-MERCH-025 | `POST /api/Merchant/CreateEntityUser` | `MerchantController.CreateEntityUser` | MerchantController.CreateEntityUser | see contract | confirmed |
| BE-API-MERCH-026 | `POST /api/Merchant/IsPINReset` | `MerchantController.IsPINReset` | MerchantController.IsPINReset | see contract | confirmed |
| BE-API-MERCH-027 | `POST /api/Merchant/ChangeMerchantPin` | `MerchantController.ChangeMerchantPin` | MerchantController.ChangeMerchantPin | see contract | confirmed |
| BE-API-MERCH-028 | `POST /api/Merchant/TransactionHistory` | `MerchantController.TransactionHistory` | MerchantController.TransactionHistory | see contract | confirmed |
| BE-API-MERCH-029 | `POST /api/Merchant/PerformanceAnalytics` | `MerchantController.PerformanceAnalytics` | MerchantController.PerformanceAnalytics | see contract | confirmed |
| BE-API-MERCH-030 | `POST /api/Merchant/dec` | `MerchantController.dec` | MerchantController.dec | see contract | partial |
| BE-API-MERCH-031 | `POST /api/Merchant/encRegisterDevice` | `MerchantController.encRegisterDevice` | MerchantController.encRegisterDevice | see contract | confirmed |
| BE-API-MERCH-032 | `POST /api/Merchant/encVerifyDevice` | `MerchantController.encVerifyDevice` | MerchantController.encVerifyDevice | see contract | confirmed |
| BE-API-MERCH-033 | `POST /api/Merchant/encGetSessionToken` | `MerchantController.encGetSessionToken` | MerchantController.encGetSessionToken | see contract | confirmed |
| BE-API-MERCH-034 | `POST /api/Merchant/encGenerateQR` | `MerchantController.encGenerateQR` | MerchantController.encGenerateQR | see contract | confirmed |
| BE-API-MERCH-035 | `POST /api/Merchant/encUpdateMerchantStatus` | `MerchantController.encUpdateMerchantStatus` | MerchantController.encUpdateMerchantStatus | see contract | confirmed |
| BE-API-MERCH-036 | `POST /api/Merchant/encIsPinReset` | `MerchantController.encIsPinReset` | MerchantController.encIsPinReset | see contract | confirmed |
| BE-API-MERCH-037 | `POST /api/DynamicQR/GenerateQR` | `DynamicQRController.GenerateQR` | DynamicQRController.GenerateQR | see contract | confirmed |
| BE-API-MERCH-038 | `POST /api/Settlement/GetTransferScheduleById` | `SettlementController.GetTransferScheduleById` | SettlementController.GetTransferScheduleById | see contract | confirmed |
| BE-API-MERCH-039 | `POST /api/Settlement/GetTransferScheduleByMSISDN` | `SettlementController.GetTransferScheduleByMSISDN` | SettlementController.GetTransferScheduleByMSISDN | see contract | confirmed |
| BE-API-MERCH-040 | `POST /api/Settlement/GetAllTransferSchedule` | `SettlementController.GetAllTransferSchedules` | SettlementController.GetAllTransferSchedules | see contract | confirmed |
| BE-API-MERCH-041 | `POST /api/Settlement/GetActiveTransferSchedule` | `SettlementController.GetActiveTransferSchedules` | SettlementController.GetActiveTransferSchedules | see contract | confirmed |
| BE-API-MERCH-042 | `POST /api/Settlement/AcceptTermsandCondition` | `SettlementController.AddSettlementTc` | SettlementController.AddSettlementTc | see contract | confirmed |
| BE-API-MERCH-043 | `POST /api/Settlement/ListSettlement` | `SettlementController.ListSettlement` | SettlementController.ListSettlement | see contract | confirmed |
| BE-API-MERCH-044 | `POST /api/Settlement/importcsv` | `SettlementController.ImportBundles` | SettlementController.ImportBundles | see contract | confirmed |
| BE-API-MERCH-045 | `POST /api/Settlement/enc` | `SettlementController.enc` | SettlementController.enc | see contract | confirmed |
| BE-API-MERCH-046 | `POST /api/Settlement/dec` | `SettlementController.dec` | SettlementController.dec | see contract | partial |

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
| `Profile` / `Profiles` | EF set |
| `MerchantQRConfiguration` / `merchantqrconfiguration` | EF set |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`ConfigAPIUrl`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `EnableLog:Warning`, `Encryption_Decryption_Key`, `FCMNotify`, `IV`, `IsRedisCluster`, `LoginURL`, `MFSUserDetails`, `MerchantR2PConfigurations`, `Partner_USSD`, `Partner_WEB`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:LogQueueName`, `RabbitMQ:LogURL`, `RabbitMQ:QueueName`, `RabbitMQ:Username`, `RedisPassword (key name)<redacted-purpose>`, `RedisURL`, `SaveLogs`, `SendAuditLogsViaService`, `SendFCMViaService`, `TANQR`, `Tanzania:<redacted-purpose>`, `Tanzania:AuthHeader`, `Tanzania:CashOut`, `Tanzania:CashOutAuthToken`, `Tanzania:CashOutFee`, `Tanzania:CheckPaymentAuthentication`, `Tanzania:ConsumerID`, `Tanzania:CreateEntityUser`, `Tanzania:GenerateQRUrl`, `Tanzania:GetSessionTokenUrl`, `Tanzania:IsPINReset`, `Tanzania:Login:Username`, `Tanzania:Login:consumerID`, `Tanzania:MSIDN`, `Tanzania:MerchantLookupUrl`

## Open questions
- Gateway public URLs not in-repo.
