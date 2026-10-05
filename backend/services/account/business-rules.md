---
kb_section: backend
type: service
ids: [BE-SVC-ACCOUNT]
service: ACCOUNT
repo: TZ-Tigo-SuperApp-Account
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 5c549d6
updated: 2026-10-05
confidence: partial
---

# Business rules — ACCOUNT

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-ACCOUNT-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
| BE-BR-ACCOUNT-002 | Blocked devices cannot call gated profile APIs | security | DeviceFilter | — | profile/device | confirmed |
