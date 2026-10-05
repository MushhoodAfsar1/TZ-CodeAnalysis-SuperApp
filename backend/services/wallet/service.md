---
kb_section: backend
type: service
ids: [BE-SVC-WALLET]
service: WALLET
repo: TZ-Tigo-SuperApp-Wallet
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 27737b1
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-WALLET TZ-Tigo-SuperApp-Wallet
**Repo:** `TZ-Tigo-SuperApp-Wallet` · **Type:** service · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `27737b1`
**Purpose:** Wallet balance and cash-out

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-WALLET-001 | POST /api/CashOut/cashOutFee | CashOutController.CashOutFee | — | none | confirmed |
| BE-API-WALLET-002 | POST /api/CashOut/cashOutPaymentV1 | CashOutController.CashOutPaymentV1 | — | none | confirmed |
| BE-API-WALLET-003 | POST /api/CashOut/cashOutPayment | CashOutController.CashOutPayment | — | none | confirmed |
| BE-API-WALLET-004 | POST /api/CashOut/encrypt | CashOutController.Encrypt | — | none | confirmed |
| BE-API-WALLET-005 | POST /api/CashOut/decrypt | CashOutController.Decrypt | — | none | confirmed |
| BE-API-WALLET-006 | POST /api/WalletBalance | WalletBalanceController.GetBalance | — | none | confirmed |
| BE-API-WALLET-007 | POST /api/WalletBalance/enc | WalletBalanceController.enc | — | none | confirmed |


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
