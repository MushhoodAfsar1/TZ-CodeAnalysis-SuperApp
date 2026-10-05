---
kb_section: backend
type: meta
ids: [BE-META-REG]
service: ALL
repo: multi
repo_ref: checked-out
repo_sha: multi
updated: 2026-10-05
confidence: confirmed
---

# Repo registry

Analyzed **as checked out** (no fetch). Porcelain recorded separately.

| Code | Repo | Type | TF | Branch | SHA | Purpose |
|---|---|---|---|---|---|---|
| IDENT | `TZ-Tigo-SuperApp-Identity` | auth/identity | net8.0 | `cursor/superapp-backend-documentation-cf53` | `e7397b0` | Identity / admin IAM |
| SESS | `TZ-Tigo-SuperApp-Session` | auth/identity | net8.0 | `cursor/superapp-backend-documentation-cf53` | `6f24061` | Mobile session JWT issuance |
| ACCOUNT | `TZ-Tigo-SuperApp-Account` | service | net8.0 | `cursor/superapp-backend-documentation-cf53` | `5c549d6` | Profile, registration, OTP, devices, QR, favourites |
| WALLET | `TZ-Tigo-SuperApp-Wallet` | service | net8.0 | `cursor/superapp-backend-documentation-cf53` | `27737b1` | Wallet balance and cash-out |
| SEND | `TZ-Tigo-SuperApp-SendMoney` | service | net8.0 | `cursor/superapp-backend-documentation-cf53` | `599771b` | P2P send money, standing orders, ATM cash-out |
| AIRTIME | `TZ-Tigo-SuperApp-AirTimeTopup` | service | net8.0 | `cursor/superapp-backend-documentation-cf53` | `7a52359` | Airtime and fiber product top-up |
| EXTPAY | `TZ-Tigo-SuperApp-ExternalPayment` | adapter/integration | net8.0 | `cursor/superapp-backend-documentation-cf53` | `51718e1` | Bill / government / external payments |
| MERCH | `TZ-Tigo-SuperApp-Merchant` | service | net8.0 | `cursor/superapp-backend-documentation-cf53` | `2367767` | Merchant QR, RTP, cash-out, settlement schedules |
| MERSET | `TZ-Tigo-SuperApp-MerchantSettlementScheduler` | batch/scheduler | net8.0 | `cursor/superapp-backend-documentation-cf53` | `d638213` | Merchant settlement scheduler |
| LOAN | `TZ-Tigo-SuperApp-Loan` | service | net8.0 | `cursor/superapp-backend-documentation-cf53` | `759a471` | Loans (device / Kitonga) |
| SAVING | `TZ-Tigo-SuperApp-Saving` | service | net8.0 | `cursor/superapp-backend-documentation-cf53` | `2ca8791` | Personal savings / Kibubu+ |
| GRPSAV | `TZ-Tigo-SuperApp-GroupSaving` | service | net8.0 | `cursor/superapp-backend-documentation-cf53` | `ed4ac20` | Group savings and group loans |
| MCHANGO | `TZ-Tigo-SuperApp-MChango` | service | net8.0 | `cursor/superapp-backend-documentation-cf53` | `7c288ab` | MChango collections (mobile + web) |
| MCHRPT | `TZ-Tigo-SuperApp-MChangoReportScheduler` | batch/scheduler | net8.0 | `cursor/superapp-backend-documentation-cf53` | `34ba77f` | MChango reports and interest |
| INSUR | `TZ-Tigo-SuperApp-Insurrance` | service | net8.0 | `cursor/superapp-backend-documentation-cf53` | `38747da` | Insurance purchase |
| VCARD | `TZ-Tigo-SuperApp-VirtualCard` | service | net8.0 | `cursor/superapp-backend-documentation-cf53` | `db358e6` | Virtual card issuance |
| DSTV | `TZ-Tigo-SuperApp-DigitalSubscription` | service | net8.0 | `cursor/superapp-backend-documentation-cf53` | `fd31aa1` | Digital / DSTV subscriptions |
| GSM | `TZ-Tigo-SuperApp-GSM` | service | net8.0 | `cursor/superapp-backend-documentation-cf53` | `13fe724` | GSM bundles and SIM self-care |
| SELFC | `TZ-Tigo-SuperApp-SelfCare` | service | net8.0 | `cursor/superapp-backend-documentation-cf53` | `a0aeca8` | Self-care (block, SMS, conversion) |
| REWARD | `TZ-Tigo-SuperApp-RewardReferral` | service | net8.0 | `cursor/superapp-backend-documentation-cf53` | `b47cb93` | Mixx points and referral rewards |
| NOTIF | `TZ-Tigo-SuperApp-Notification` | service | net8.0 | `cursor/superapp-backend-documentation-cf53` | `b7c98ec` | Notifications and FCM |
| NOTSCH | `TZ-Tigo-SuperApp-Notification-Scheduler` | batch/scheduler | net8.0 | `cursor/superapp-backend-documentation-cf53` | `72838eb` | Notification delivery scheduler |
| AUDIT | `TZ-Tigo-SuperApp-AuditLogs` | service | net8.0 | `cursor/superapp-backend-documentation-cf53` | `eb87819` | Audit log ingestion / query |
| EXPENSE | `TZ-Tigo-SuperApp-Expense` | service | net8.0 | `cursor/superapp-backend-documentation-cf53` | `e821ac9` | Expense and advance salary |
| GAMES | `TZ-Tigo-SuperApp-Games` | service | net8.0 | `cursor/superapp-backend-documentation-cf53` | `10c8daa` | Games |
| RESERV | `TZ-Tigo-SuperApp-Reservation` | service | net8.0 | `cursor/superapp-backend-documentation-cf53` | `dfd072a` | Movies and bus tickets |
| STOCK | `TZ-Tigo-SuperApp-Stock` | service | net8.0 | `cursor/superapp-backend-documentation-cf53` | `10f0a62` | Stock and market data |
| PORTAL | `TZ-Tigo-SuperApp-WebPortal` | other | unknown | `cursor/superapp-backend-documentation-cf53` | `bb69e15` | Angular admin portal (atlantis) |
| CONFIG | `TZ-Tigo-SuperApp-Configuration` | config/infra | net8.0 | `cursor/superapp-backend-documentation-cf53` | `9c00072` | Configuration / BO / app CMS APIs |
