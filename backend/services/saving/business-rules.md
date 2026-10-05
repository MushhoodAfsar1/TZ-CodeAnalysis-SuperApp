---
kb_section: backend
type: service
ids: [BE-SVC-SAVING]
service: SAVING
repo: TZ-Tigo-SuperApp-Saving
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 2ca8791
updated: 2026-10-05
confidence: partial
---

# Business rules — SAVING

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-SAVING-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
