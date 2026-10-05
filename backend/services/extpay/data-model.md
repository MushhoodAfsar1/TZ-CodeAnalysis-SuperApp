---
kb_section: backend
type: service
ids: [BE-SVC-EXTPAY]
service: EXTPAY
repo: TZ-Tigo-SuperApp-ExternalPayment
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 51718e1
updated: 2026-10-05
confidence: partial
---

# Data model — EXTPAY

| Entity | Table | Source |
|---|---|---|
| `TZExternalPaymentEFContext` | `—` | `TZTigoSuperAppExternalPayment/Domain/DBContext/TZExternalPaymentEFContext.cs` |
| `ConfigurationEFContext` | `—` | `TZTigoSuperAppExternalPayment/Domain/DBContext/ConfigurationEFContext.cs` |
| `AccountEFContext` | `—` | `TZTigoSuperAppExternalPayment/Domain/DBContext/AccountEFContext.cs` |
| `Tokens` | `—` | `TZTigoSuperAppExternalPayment/Domain/Entity/Tokens.cs` |
| `BillPayment` | `—` | `TZTigoSuperAppExternalPayment/Domain/Entity/BillPayment.cs` |
| `govpayshortcode` | `—` | `TZTigoSuperAppExternalPayment/Domain/Entity/GovPayShortCode.cs` |
| `BaseEntity` | `—` | `TZTigoSuperAppExternalPayment/Domain/Entity/BaseEntity.cs` |
| `SubmitBillPaymentRepository` | `—` | `TZTigoSuperAppExternalPayment/Domain/Repositories/SubmitBillPaymentRepository.cs` |
| `ValidateBillerDetailsRepository` | `—` | `TZTigoSuperAppExternalPayment/Domain/Repositories/ValidateBillerDetailsRepository.cs` |
