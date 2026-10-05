---
kb_section: backend
type: service
ids: [BE-SVC-STOCK]
service: STOCK
repo: TZ-Tigo-SuperApp-Stock
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 10f0a62
updated: 2026-10-05
confidence: partial
---

# Business rules — STOCK

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-STOCK-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
