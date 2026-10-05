---
kb_section: backend
type: service
ids: [BE-SVC-INSUR]
service: INSUR
repo: TZ-Tigo-SuperApp-Insurrance
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 38747da
updated: 2026-10-05
confidence: partial
---

# Business rules — INSUR

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-INSUR-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
