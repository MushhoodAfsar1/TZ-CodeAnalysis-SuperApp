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

# Business rules — SEND

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-SEND-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
| BE-BR-SEND-003 | TANQR shortCode maps target MSISDN first-3 digits via `tanqrshortcode`; miss → Invalid Alias | validation | SendMoneyRepository | TANQR | Verify/Transfer | confirmed |
| BE-BR-SEND-004 | Rail: `userCaseName==sendmoney` or shortCode in 50001/50024/50058 uses Tigo SOAP; else other/bill SOAP | product | SendMoneyRepository | Transfer/Verify URL keys | Verify/Transfer | confirmed |
| BE-BR-SEND-005 | InclCOFee true forces ShortCode `50001` on fee/pay Tigo rail | product | SendMoneyRepository | — | Verify/Transfer | confirmed |
| BE-BR-SEND-006 | MMP success when ResultCode in `0` (verify) or `0\|200102\|200109\|99999` (transfer) | validation | SendMoneyRepository | — | Verify/Transfer | confirmed |
| BE-BR-SEND-007 | Tip leg aborted if prior payment leg failed | validation | TransferSendMoney | — | BE-API-SEND-011 | confirmed |
