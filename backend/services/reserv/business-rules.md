---
kb_section: backend
type: service
ids: [BE-SVC-RESERV]
service: RESERV
repo: TZ-Tigo-SuperApp-Reservation
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: dfd072a
updated: 2026-10-05
confidence: partial
---

# Business rules — RESERV

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-RESERV-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
