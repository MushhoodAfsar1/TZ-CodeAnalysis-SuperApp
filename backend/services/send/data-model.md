---
kb_section: backend
type: service
ids: [BE-SVC-SEND]
service: SEND
repo: TZ-Tigo-SuperApp-SendMoney
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 599771b
updated: 2026-10-05
confidence: partial
---

# Data model — SEND

| Entity | Table | Source |
|---|---|---|
| `TZAccountEFContext` | `—` | `TZTigoSuperAppSendMoney/Domain/DBContext/TZAccountEFContext.cs` |
| `TZSendMoneyEFContext` | `—` | `TZTigoSuperAppSendMoney/Domain/DBContext/TZSendMoneyEFContext.cs` |
| `StandingOrder` | `—` | `TZTigoSuperAppSendMoney/Domain/Entity/StandingOrder.cs` |
| `BaseEntity` | `—` | `TZTigoSuperAppSendMoney/Domain/Entity/BaseEntity.cs` |
| `Transfer` | `—` | `TZTigoSuperAppSendMoney/Domain/Entity/SendMoney/Transfer.cs` |
| `ATMTransactions` | `—` | `TZTigoSuperAppSendMoney/Domain/Entity/SendMoney/ATMTransactions.cs` |
| `giftmoneyrecord` | `—` | `TZTigoSuperAppSendMoney/Domain/Entity/SendMoney/giftmoneyrecord.cs` |
| `tanqrshortcode` | `—` | `TZTigoSuperAppSendMoney/Domain/Entity/SendMoney/tanqrshortcode.cs` |
| `Profile` | `—` | `TZTigoSuperAppSendMoney/Domain/Entity/Account/Profile.cs` |
| `standingordermapping` | `—` | `TZTigoSuperAppSendMoney/Domain/Entity/Account/StandingOrderMapping.cs` |
| `Tokens` | `—` | `TZTigoSuperAppSendMoney/Domain/Entity/Account/Tokens.cs` |
