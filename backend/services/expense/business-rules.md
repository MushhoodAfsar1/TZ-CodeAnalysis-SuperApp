---
kb_section: backend
type: service
ids: [BE-SVC-EXPENSE]
service: EXPENSE
repo: TZ-Tigo-SuperApp-Expense
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: e821ac9
updated: 2026-10-05
confidence: partial
---

# Business rules — EXPENSE

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-EXPENSE-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
