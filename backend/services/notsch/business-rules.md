---
kb_section: backend
type: service
ids: [BE-SVC-NOTSCH]
service: NOTSCH
repo: TZ-Tigo-SuperApp-Notification-Scheduler
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 72838eb
updated: 2026-10-05
confidence: partial
---

# Business rules — NOTSCH

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-NOTSCH-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
