---
kb_section: backend
type: service
ids: [BE-SVC-WALLET]
service: WALLET
repo: TZ-Tigo-SuperApp-Wallet
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 27737b1
updated: 2026-10-05
confidence: confirmed
---

# Integrations — WALLET

Hosts/secrets omitted.

| ID | Name | How | Evidence |
|---|---|---|---|
| BE-INT-WALLET-001 | HttpClient `CMM` | named client; base URL from config key (value omitted) | Program/DI |
| BE-INT-WALLET-002 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}` | outbound HTTP path shape | static string |
| BE-INT-WALLET-003 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}/{service}/{serviceMethod}` | outbound HTTP path shape | static string |
| BE-INT-WALLET-004 | MMP SOAP CalculateFee | URL key `CashOutFee`; auth `Tanzania:Username\|Password\|ConsumerID` | CashOutService.CashOutFee |
| BE-INT-WALLET-005 | MMP SOAP CashoutRequest | URL key `CashOutPayment` | CashOutService.CashOutPayment / V1 |
| BE-INT-WALLET-006 | MMP XML GetBalance | URL key `MTPGGetBalance`; `Tanzania:ChannelUser`, `Tanzania:ChannerPass` | WalletBalanceRepository.GetBalance |
