---
kb_section: backend
type: service
ids: [BE-SVC-VCARD]
service: VCARD
repo: TZ-Tigo-SuperApp-VirtualCard
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: db358e6
updated: 2026-10-05
confidence: partial
---

# Business rules — VCARD

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-VCARD-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
