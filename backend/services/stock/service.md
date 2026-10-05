---
kb_section: backend
type: service
ids: [BE-SVC-STOCK]
service: STOCK
repo: TZ-Tigo-SuperApp-Stock
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 10f0a62
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-STOCK TZ-Tigo-SuperApp-Stock
**Repo:** `TZ-Tigo-SuperApp-Stock` · **Type:** service · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `10f0a62`
**Purpose:** Stock / CDS

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-STOCK-001 | POST /api/MarketData | MarketDataController.GetMarketData | — | none | confirmed |
| BE-API-STOCK-002 | POST /api/MarketData | MarketDataController.GetMarketDataStats | — | none | confirmed |
| BE-API-STOCK-003 | POST /api/MarketData | MarketDataController.GetCompanies | — | none | confirmed |
| BE-API-STOCK-004 | POST /api/Stock | StockController.RegisterStockAccount | — | none | confirmed |
| BE-API-STOCK-005 | POST /api/Stock | StockController.FetchDashboardData | — | none | confirmed |
| BE-API-STOCK-006 | POST /api/Stock | StockController.GetStockBrokers | — | none | confirmed |
| BE-API-STOCK-007 | POST /api/Stock | StockController.GetStockLivePrices | — | none | confirmed |
| BE-API-STOCK-008 | POST /api/Stock | StockController.GetStockInvestorHoldings | — | none | confirmed |
| BE-API-STOCK-009 | POST /api/Stock | StockController.GetStockCdsClients | — | none | confirmed |
| BE-API-STOCK-010 | POST /api/Stock | StockController.VerifyStockAccount | — | none | confirmed |
| BE-API-STOCK-011 | POST /api/Stock | StockController.CreateSellOrder | — | none | confirmed |
| BE-API-STOCK-012 | POST /api/Stock | StockController.GetSellOrder | — | none | confirmed |
| BE-API-STOCK-013 | POST /api/Stock | StockController.CreateBuyOrder | — | none | confirmed |
| BE-API-STOCK-014 | POST /api/Stock | StockController.GetBuyOrder | — | none | confirmed |
| BE-API-STOCK-015 | POST /api/Stock | StockController.GetOrders | — | none | confirmed |
| BE-API-STOCK-016 | POST /api/Stock | StockController.GetBuyOrderReference | — | none | confirmed |
| BE-API-STOCK-017 | POST /api/Stock | StockController.ValidateBillerDetail | — | none | confirmed |
| BE-API-STOCK-018 | POST /api/Stock | StockController.SubmitBillPayment | — | none | confirmed |


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
