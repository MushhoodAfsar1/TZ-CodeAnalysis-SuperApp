---
kb_section: backend
type: service
ids: [BE-SVC-SESS]
service: SESS
repo: TZ-Tigo-SuperApp-Session
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 6f24061
updated: 2026-10-05
confidence: partial
---

# Business rules — SESS

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-SESS-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
