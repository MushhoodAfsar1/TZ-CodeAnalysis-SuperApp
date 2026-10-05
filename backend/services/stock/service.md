---
kb_section: backend
type: service
ids: [BE-SVC-STOCK]
service: STOCK
repo: TZ-Tigo-SuperApp-Stock
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 10f0a62
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-STOCK Stock and market data
**Repo:** `TZ-Tigo-SuperApp-Stock` · **Type:** service · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `10f0a62`
**Purpose:** Stock and market data

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** MassTransit.RabbitMQ, Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-STOCK-001 | `POST /api/Stock/RegisterStockAccount` | `StockController.RegisterStockAccount` | StockController.RegisterStockAccount | see contract | confirmed |
| BE-API-STOCK-002 | `POST /api/Stock/FetchDashboardData` | `StockController.FetchDashboardData` | StockController.FetchDashboardData | see contract | confirmed |
| BE-API-STOCK-003 | `POST /api/Stock/GetStockBrokers` | `StockController.GetStockBrokers` | StockController.GetStockBrokers | see contract | confirmed |
| BE-API-STOCK-004 | `POST /api/Stock/GetStockLivePrices` | `StockController.GetStockLivePrices` | StockController.GetStockLivePrices | see contract | confirmed |
| BE-API-STOCK-005 | `POST /api/Stock/GetStockInvestorHoldings` | `StockController.GetStockInvestorHoldings` | StockController.GetStockInvestorHoldings | see contract | confirmed |
| BE-API-STOCK-006 | `POST /api/Stock/GetStockCdsClients` | `StockController.GetStockCdsClients` | StockController.GetStockCdsClients | see contract | confirmed |
| BE-API-STOCK-007 | `POST /api/Stock/VerifyStockAccount` | `StockController.VerifyStockAccount` | StockController.VerifyStockAccount | see contract | confirmed |
| BE-API-STOCK-008 | `POST /api/Stock/CreateSellOrder` | `StockController.CreateSellOrder` | StockController.CreateSellOrder | see contract | confirmed |
| BE-API-STOCK-009 | `POST /api/Stock/GetSellOrder` | `StockController.GetSellOrder` | StockController.GetSellOrder | see contract | confirmed |
| BE-API-STOCK-010 | `POST /api/Stock/CreateBuyOrder` | `StockController.CreateBuyOrder` | StockController.CreateBuyOrder | see contract | confirmed |
| BE-API-STOCK-011 | `POST /api/Stock/GetBuyOrder` | `StockController.GetBuyOrder` | StockController.GetBuyOrder | see contract | confirmed |
| BE-API-STOCK-012 | `POST /api/Stock/GetOrders` | `StockController.GetOrders` | StockController.GetOrders | see contract | confirmed |
| BE-API-STOCK-013 | `POST /api/Stock/GetBuyOrderReference` | `StockController.GetBuyOrderReference` | StockController.GetBuyOrderReference | see contract | confirmed |
| BE-API-STOCK-014 | `POST /api/Stock/ValidateBillerDetails` | `StockController.ValidateBillerDetail` | StockController.ValidateBillerDetail | see contract | confirmed |
| BE-API-STOCK-015 | `POST /api/Stock/SubmitBillPayment` | `StockController.SubmitBillPayment` | StockController.SubmitBillPayment | see contract | confirmed |
| BE-API-STOCK-016 | `POST /api/MarketData/GetMarketData` | `MarketDataController.GetMarketData` | MarketDataController.GetMarketData | see contract | confirmed |
| BE-API-STOCK-017 | `POST /api/MarketData/GetMarketDataStats` | `MarketDataController.GetMarketDataStats` | MarketDataController.GetMarketDataStats | see contract | confirmed |
| BE-API-STOCK-018 | `POST /api/MarketData/GetCompanies` | `MarketDataController.GetCompanies` | MarketDataController.GetCompanies | see contract | confirmed |

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
| `StockUsers` / `stockUsers` | EF set |
| `BillPayment` / `billPayments` | EF set |
| `StockData` / `stockData` | EF set |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`ConfigAPIUrl`, `CreateBuyOrder`, `CreateSellOrder`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `Encryption_Decryption_Key`, `GetBuyOrder`, `GetBuyOrderReference`, `GetSellOrder`, `IV`, `IsRedisCluster`, `MTPGBillQuery`, `MarketCompaniesUrl`, `MarketData`, `MarketDataStats`, `OTPSource`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:IsHttpsRabbitMQ`, `RabbitMQ:LogQueueName`, `RabbitMQ:Port`, `RabbitMQ:URL`, `RabbitMQ:Username`, `RedisPassword (key name)<redacted-purpose>`, `RedisURL`, `SaveLogs`, `SendAuditLogsViaService`, `SendEMail`, `SendSMS`, `SuperAppMTPGPayment:URL`, `SuperAppMTPGPayment:consumerID`, `SuperAppMTPGPayment:terminalType`, `SuperAppSelfcareLukuToken`, `SuperAppStockBrokers`, `SuperAppStockCdsClient`, `SuperAppStockGainerandLosers`, `SuperAppStockInvestorHoldings`, `SuperAppStockLivePrices`, `SuperAppStockMarketOverview`, `SuperAppStockMovers`

## Open questions
- Gateway public URLs not in-repo.
