---
kb_section: backend
type: meta
ids: [BE-META-REG]
service: ALL
repo: multi
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: multi
updated: 2026-10-05
confidence: confirmed
---
# Repo registry

Checkout branch (platform): `cursor/superapp-backend-documentation-6fa7`. Analysis is read-only on these SHAs.

| Code | Repo | Type | SHA | Ctrl | HTTP | Packages (subset) | Purpose |
|---|---|---|---|---:|---:|---|---|
| IDENT | TZ-Tigo-SuperApp-Identity | auth/identity | e7397b0 | 4 | 34 | `MassTransit.RabbitMQ,Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.InMemory,Microsoft.EntityFrameworkCore.Tools,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact,StackExchange.Redis` | Identity / KYC / portal login (ASP.NET Identity + LDAP) |
| SESS | TZ-Tigo-SuperApp-Session | auth/identity | 6f24061 | 1 | 4 | `MassTransit.RabbitMQ,Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.Design,Microsoft.EntityFrameworkCore.InMemory,Microsoft.EntityFrameworkCore.Tools,Serilog,Serilog.AspNetCore,Serilog.Filters.Expressions` | Mobile session JWT issue/refresh |
| ACCOUNT | TZ-Tigo-SuperApp-Account | service | 5c549d6 | 6 | 51 | `MassTransit.RabbitMQ,Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.InMemory,Microsoft.EntityFrameworkCore.Tools,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact,StackExchange.Redis` | Accounts, profile, devices, OTP, QR, favourites |
| WALLET | TZ-Tigo-SuperApp-Wallet | service | 27737b1 | 2 | 7 | `Dapper,MassTransit.RabbitMQ,Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.InMemory,Microsoft.EntityFrameworkCore.Tools,Serilog,Serilog.AspNetCore,Serilog.Filters.Expressions` | Wallet balance and cash-out |
| SEND | TZ-Tigo-SuperApp-SendMoney | service | 599771b | 3 | 15 | `MassTransit.RabbitMQ,Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.InMemory,Microsoft.EntityFrameworkCore.Tools,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact,StackExchange.Redis` | Send money / P2P |
| AIRTIME | TZ-Tigo-SuperApp-AirTimeTopup | service | 7a52359 | 2 | 10 | `MassTransit.RabbitMQ,Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.InMemory,Microsoft.EntityFrameworkCore.Tools,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact,StackExchange.Redis` | Airtime top-up |
| EXTPAY | TZ-Tigo-SuperApp-ExternalPayment | adapter/integration | 51718e1 | 1 | 6 | `Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.Tools,RabbitMQ.Client,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact,StackExchange.Redis` | External / bill payments |
| MERCH | TZ-Tigo-SuperApp-Merchant | service | 2367767 | 7 | 46 | `Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.Tools,RabbitMQ.Client,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact,StackExchange.Redis` | Merchant |
| MERSET | TZ-Tigo-SuperApp-MerchantSettlementScheduler | batch/scheduler | d638213 | 0 | 0 | `Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.Tools,RabbitMQ.Client,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact,StackExchange.Redis` | Merchant settlement jobs |
| LOAN | TZ-Tigo-SuperApp-Loan | service | 759a471 | 3 | 24 | `MassTransit.RabbitMQ,Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.Tools,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact,StackExchange.Redis` | Loans |
| SAVING | TZ-Tigo-SuperApp-Saving | service | 2ca8791 | 2 | 8 | `Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.Tools,RabbitMQ.Client,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact,StackExchange.Redis` | Savings |
| GRPSAV | TZ-Tigo-SuperApp-GroupSaving | service | ed4ac20 | 4 | 65 | `MassTransit.RabbitMQ,Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.Tools,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact,StackExchange.Redis` | Group savings |
| MCHANGO | TZ-Tigo-SuperApp-MChango | service | 7c288ab | 14 | 64 | `FluentValidation,FluentValidation.AspNetCore,Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.InMemory,Microsoft.EntityFrameworkCore.Tools,RabbitMQ.Client,Serilog.AspNetCore,Serilog.Filters.Expressions` | MChango collections |
| MCHRPT | TZ-Tigo-SuperApp-MChangoReportScheduler | batch/scheduler | 34ba77f | 0 | 0 | `FluentValidation,FluentValidation.AspNetCore,Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.Tools,RabbitMQ.Client,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact` | MChango report jobs |
| INSUR | TZ-Tigo-SuperApp-Insurrance | service | 38747da | 2 | 13 | `MassTransit.RabbitMQ,Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.Tools,RabbitMQ.Client,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact,StackExchange.Redis` | Insurance |
| VCARD | TZ-Tigo-SuperApp-VirtualCard | service | db358e6 | 1 | 9 | `Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.Tools,RabbitMQ.Client,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact,StackExchange.Redis` | Virtual cards |
| DSTV | TZ-Tigo-SuperApp-DigitalSubscription | service | fd31aa1 | 1 | 7 | `MassTransit.RabbitMQ,Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.Tools,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact,StackExchange.Redis` | Digital subscriptions |
| GSM | TZ-Tigo-SuperApp-GSM | service | 13fe724 | 2 | 16 | `MassTransit.RabbitMQ,Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.InMemory,Microsoft.EntityFrameworkCore.Tools,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact,StackExchange.Redis` | GSM / SIM |
| SELFC | TZ-Tigo-SuperApp-SelfCare | service | a0aeca8 | 4 | 57 | `Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.InMemory,Microsoft.EntityFrameworkCore.Tools,RabbitMQ.Client,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact,StackExchange.Redis` | Self-care |
| REWARD | TZ-Tigo-SuperApp-RewardReferral | service | b47cb93 | 3 | 22 | `MassTransit.RabbitMQ,Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.InMemory,Microsoft.EntityFrameworkCore.Tools,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact,StackExchange.Redis` | Rewards / referral |
| NOTIF | TZ-Tigo-SuperApp-Notification | service | b7c98ec | 4 | 19 | `MassTransit,MassTransit.RabbitMQ,Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.InMemory,Microsoft.EntityFrameworkCore.Tools,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact` | Notifications |
| NOTSCH | TZ-Tigo-SuperApp-Notification-Scheduler | batch/scheduler | 72838eb | 0 | 0 | `FluentValidation,FluentValidation.AspNetCore,Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.Tools,RabbitMQ.Client,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact` | Notification scheduler jobs |
| AUDIT | TZ-Tigo-SuperApp-AuditLogs | service | eb87819 | 1 | 1 | `MassTransit,MassTransit.RabbitMQ,Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.InMemory,Microsoft.EntityFrameworkCore.Tools,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact` | Audit logs |
| EXPENSE | TZ-Tigo-SuperApp-Expense | service | e821ac9 | 2 | 15 | `MassTransit.RabbitMQ,Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.InMemory,Microsoft.EntityFrameworkCore.Tools,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact,StackExchange.Redis` | Expenses |
| GAMES | TZ-Tigo-SuperApp-Games | service | 10c8daa | 1 | 8 | `Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.Tools,RabbitMQ.Client,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact,StackExchange.Redis` | Games |
| RESERV | TZ-Tigo-SuperApp-Reservation | service | dfd072a | 2 | 13 | `MassTransit.RabbitMQ,Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.Tools,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact,StackExchange.Redis` | Reservations |
| STOCK | TZ-Tigo-SuperApp-Stock | service | 10f0a62 | 2 | 18 | `MassTransit.RabbitMQ,Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.Tools,Serilog.AspNetCore,Serilog.Filters.Expressions,Serilog.Formatting.Compact,StackExchange.Redis` | Stock / CDS |
| PORTAL | TZ-Tigo-SuperApp-WebPortal | other | bb69e15 | 0 | 0 | `` | Angular admin portal (atlantis) |
| CONFIG | TZ-Tigo-SuperApp-Configuration | config/infra | 9c00072 | 97 | 432 | `Dapper,MassTransit.RabbitMQ,Microsoft.EntityFrameworkCore,Microsoft.EntityFrameworkCore.InMemory,Microsoft.EntityFrameworkCore.Tools,Serilog,Serilog.AspNetCore,Serilog.Filters.Expressions` | Shared configuration APIs |
