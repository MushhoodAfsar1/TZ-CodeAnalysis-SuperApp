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

# Business rules — WALLET

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-WALLET-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
| BE-BR-WALLET-002 | Cash-out fee succeeds only when SOAP code is `calculatefee-3031-0000-s`; SOAP PIN is hard-coded `0000` | validation | CashOutService.CashOutFee | CashOutFee | BE-API-WALLET-001 | confirmed |
| BE-BR-WALLET-003 | Cash-out pay: `walletmanagement-2004-0000-s` success+FCM. V1 treats `2004-6001-w` as success; V0 remaps to `walletmanagement-20103-w` fail | validation | CashOutController / CashOutService | CashOutPayment | BE-API-WALLET-002/003 | confirmed |
| BE-BR-WALLET-004 | Overdraft brand is sent on CashOutPaymentV1 SOAP only, not V0 | product | CashOutService.CashOutPaymentV1 | CashOutPayment | BE-API-WALLET-002 | confirmed |
| BE-BR-WALLET-005 | GetBalance succeeds only when MMP `resultCode=="0"` | validation | WalletBalanceRepository | MTPGGetBalance | BE-API-WALLET-006 | confirmed |
