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
| AIRTIME | TZ-Tigo-SuperApp-AirTimeTopup | inventoried | 7a52359 | 10 | 0 | 2 | deep pass pending |
| EXTPAY | TZ-Tigo-SuperApp-ExternalPayment | inventoried | 51718e1 | 6 | 0 | 1 | deep pass pending |
| MERCH | TZ-Tigo-SuperApp-Merchant | inventoried | 2367767 | 46 | 0 | 7 | deep pass pending |
| MERSET | TZ-Tigo-SuperApp-MerchantSettlementScheduler | inventoried | d638213 | 0 | 0 | 0 | deep pass pending |
| LOAN | TZ-Tigo-SuperApp-Loan | inventoried | 759a471 | 24 | 0 | 3 | deep pass pending |
| SAVING | TZ-Tigo-SuperApp-Saving | inventoried | 2ca8791 | 8 | 0 | 2 | deep pass pending |
| GRPSAV | TZ-Tigo-SuperApp-GroupSaving | inventoried | ed4ac20 | 65 | 0 | 4 | deep pass pending |
| MCHANGO | TZ-Tigo-SuperApp-MChango | inventoried | 7c288ab | 64 | 0 | 14 | deep pass pending |
| MCHRPT | TZ-Tigo-SuperApp-MChangoReportScheduler | inventoried | 34ba77f | 0 | 0 | 0 | deep pass pending |
| INSUR | TZ-Tigo-SuperApp-Insurrance | inventoried | 38747da | 13 | 0 | 2 | deep pass pending |
| VCARD | TZ-Tigo-SuperApp-VirtualCard | inventoried | db358e6 | 9 | 0 | 1 | deep pass pending |
| DSTV | TZ-Tigo-SuperApp-DigitalSubscription | inventoried | fd31aa1 | 7 | 0 | 1 | deep pass pending |
| GSM | TZ-Tigo-SuperApp-GSM | inventoried | 13fe724 | 16 | 0 | 2 | deep pass pending |
| SELFC | TZ-Tigo-SuperApp-SelfCare | inventoried | a0aeca8 | 57 | 0 | 4 | deep pass pending |
| REWARD | TZ-Tigo-SuperApp-RewardReferral | inventoried | b47cb93 | 22 | 0 | 3 | deep pass pending |
| NOTIF | TZ-Tigo-SuperApp-Notification | inventoried | b7c98ec | 19 | 0 | 4 | deep pass pending |
| NOTSCH | TZ-Tigo-SuperApp-Notification-Scheduler | inventoried | 72838eb | 0 | 0 | 0 | deep pass pending |
| AUDIT | TZ-Tigo-SuperApp-AuditLogs | inventoried | eb87819 | 1 | 0 | 1 | deep pass pending |
| EXPENSE | TZ-Tigo-SuperApp-Expense | inventoried | e821ac9 | 15 | 0 | 2 | deep pass pending |
| GAMES | TZ-Tigo-SuperApp-Games | inventoried | 10c8daa | 8 | 0 | 1 | deep pass pending |
| RESERV | TZ-Tigo-SuperApp-Reservation | inventoried | dfd072a | 13 | 0 | 2 | deep pass pending |
| STOCK | TZ-Tigo-SuperApp-Stock | inventoried | 10f0a62 | 18 | 0 | 2 | deep pass pending |
| PORTAL | TZ-Tigo-SuperApp-WebPortal | inventoried | bb69e15 | 0 | 0 | 0 | deep pass pending |
| CONFIG | TZ-Tigo-SuperApp-Configuration | inventoried | 9c00072 | 432 | 0 | 97 | deep pass pending |

HTTP found via `[HttpGet|Post|Put|Delete|Patch]` on `*Controller.cs`.
