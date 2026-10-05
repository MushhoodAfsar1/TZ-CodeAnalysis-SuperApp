---
kb_section: backend
type: service
ids: [BE-SVC-NOTIF]
service: NOTIF
repo: TZ-Tigo-SuperApp-Notification
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: b7c98ec
updated: 2026-10-05
confidence: partial
---

# Business rules — NOTIF

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-NOTIF-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
