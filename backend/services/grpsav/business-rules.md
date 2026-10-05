---
kb_section: backend
type: service
ids: [BE-SVC-GRPSAV]
service: GRPSAV
repo: TZ-Tigo-SuperApp-GroupSaving
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: ed4ac20
updated: 2026-10-05
confidence: partial
---

# Business rules — GRPSAV

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-GRPSAV-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
