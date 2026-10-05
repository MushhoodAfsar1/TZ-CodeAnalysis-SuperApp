---
kb_section: backend
type: service
ids: [BE-SVC-IDENT]
service: IDENT
repo: TZ-Tigo-SuperApp-Identity
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: e7397b0
updated: 2026-10-05
confidence: partial
---

# Business rules — IDENT

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-IDENT-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
