---
kb_section: backend
type: meta
ids: [BE-META-COV]
service: ALL
repo: multi
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: multi
updated: 2026-10-05
confidence: confirmed
---
# Coverage

| Code | Repo | Status | analyzed_sha | HTTP found | APIs documented | Controllers | Notes |
|---|---|---|---|---:|---:|---:|---|
| IDENT | TZ-Tigo-SuperApp-Identity | deep-analyzed | e7397b0 | 34 | 34 | 4 |  |
| SESS | TZ-Tigo-SuperApp-Session | deep-analyzed | 6f24061 | 4 | 4 | 1 |  |
| ACCOUNT | TZ-Tigo-SuperApp-Account | deep-analyzed | 5c549d6 | 51 | 51 | 6 |  |
| WALLET | TZ-Tigo-SuperApp-Wallet | deep-analyzed | 27737b1 | 7 | 7 | 2 |  |
| SEND | TZ-Tigo-SuperApp-SendMoney | deep-analyzed | 599771b | 15 | 15 | 3 |  |
| AIRTIME | TZ-Tigo-SuperApp-AirTimeTopup | deep-analyzed | 7a52359 | 10 | 10 | 2 |  |
| EXTPAY | TZ-Tigo-SuperApp-ExternalPayment | deep-analyzed | 51718e1 | 6 | 6 | 1 |  |
| MERCH | TZ-Tigo-SuperApp-Merchant | deep-analyzed | 2367767 | 46 | 46 | 7 |  |
| MERSET | TZ-Tigo-SuperApp-MerchantSettlementScheduler | inventoried | d638213 | 0 | 0 | 0 | jobs.md: BE-JOB-MERSET-001 |
| LOAN | TZ-Tigo-SuperApp-Loan | deep-analyzed | 759a471 | 24 | 24 | 3 |  |
| SAVING | TZ-Tigo-SuperApp-Saving | deep-analyzed | 2ca8791 | 8 | 8 | 2 |  |
| GRPSAV | TZ-Tigo-SuperApp-GroupSaving | deep-analyzed | ed4ac20 | 65 | 65 | 4 |  |
| MCHANGO | TZ-Tigo-SuperApp-MChango | deep-analyzed | 7c288ab | 64 | 64 | 14 |  |
| MCHRPT | TZ-Tigo-SuperApp-MChangoReportScheduler | inventoried | 34ba77f | 0 | 0 | 0 | jobs.md: BE-JOB-MCHRPT-001/002 |
| INSUR | TZ-Tigo-SuperApp-Insurrance | deep-analyzed | 38747da | 13 | 13 | 2 |  |
| VCARD | TZ-Tigo-SuperApp-VirtualCard | deep-analyzed | db358e6 | 9 | 9 | 1 |  |
| DSTV | TZ-Tigo-SuperApp-DigitalSubscription | deep-analyzed | fd31aa1 | 7 | 7 | 1 |  |
| GSM | TZ-Tigo-SuperApp-GSM | deep-analyzed | 13fe724 | 16 | 16 | 2 |  |
| SELFC | TZ-Tigo-SuperApp-SelfCare | deep-analyzed | a0aeca8 | 57 | 57 | 4 |  |
| REWARD | TZ-Tigo-SuperApp-RewardReferral | deep-analyzed | b47cb93 | 22 | 22 | 3 |  |
| NOTIF | TZ-Tigo-SuperApp-Notification | deep-analyzed | b7c98ec | 19 | 19 | 4 |  |
| NOTSCH | TZ-Tigo-SuperApp-Notification-Scheduler | inventoried | 72838eb | 0 | 0 | 0 | jobs.md: BE-JOB-NOTSCH-001 |
| AUDIT | TZ-Tigo-SuperApp-AuditLogs | deep-analyzed | eb87819 | 1 | 1 | 1 |  |
| EXPENSE | TZ-Tigo-SuperApp-Expense | deep-analyzed | e821ac9 | 15 | 15 | 2 |  |
| GAMES | TZ-Tigo-SuperApp-Games | deep-analyzed | 10c8daa | 8 | 8 | 1 |  |
| RESERV | TZ-Tigo-SuperApp-Reservation | deep-analyzed | dfd072a | 13 | 13 | 2 |  |
| STOCK | TZ-Tigo-SuperApp-Stock | deep-analyzed | 10f0a62 | 18 | 18 | 2 |  |
| PORTAL | TZ-Tigo-SuperApp-WebPortal | inventoried | bb69e15 | 0 | 0 | 0 | deep pass pending |
| CONFIG | TZ-Tigo-SuperApp-Configuration | deep-analyzed | 9c00072 | 432 | 419 | 97 | 13 actions not parsed (non-standard signatures); see BE-GAP-004 |

HTTP found via `[HttpGet|Post|Put|Delete|Patch]` on `*Controller.cs`.
