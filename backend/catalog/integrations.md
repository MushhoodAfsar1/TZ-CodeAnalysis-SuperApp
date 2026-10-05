---
kb_section: backend
type: catalog
ids: [BE-CAT-INT]
service: ALL
repo: multi
repo_ref: checked-out
repo_sha: multi
updated: 2026-10-05
confidence: partial
---

# Integrations

Named HttpClients: `CMM`→CONFIG, `SMM`→SESS (Account), `IdentityApi`→IDENT (CONFIG). External MMP/Tigopesa/NIDA/biller URLs are config-driven; hosts omitted. Money-path URL **keys** (not hosts): WALLET `CashOutFee`/`CashOutPayment`/`MTPGGetBalance`; SEND `TransferSendMoneyTigoToTigoURL`/`TransferSendMoneyTigoToOtherURL`/`TransactionStatus`; AIRTIME `AirTimeTopUp`/`MTPGPaymentRequest:URL`; EXTPAY `SuperAppMTPGPayment`/`BankTransferPayment`/`GovernmentInquirytoGEPG`. See each `services/*/integrations.md`.
