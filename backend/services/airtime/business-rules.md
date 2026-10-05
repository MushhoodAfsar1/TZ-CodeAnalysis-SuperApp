---
kb_section: backend
type: service
ids: [BE-SVC-AIRTIME]
service: AIRTIME
repo: TZ-Tigo-SuperApp-AirTimeTopup
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 7a52359
updated: 2026-10-05
confidence: partial
---

# Business rules — AIRTIME

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-AIRTIME-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
