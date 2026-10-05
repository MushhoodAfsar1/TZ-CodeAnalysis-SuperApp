---
kb_section: backend
type: service
ids: [BE-SVC-MERCH]
service: MERCH
repo: TZ-Tigo-SuperApp-Merchant
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 2367767
updated: 2026-10-05
confidence: partial
---

# Business rules — MERCH

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-MERCH-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
