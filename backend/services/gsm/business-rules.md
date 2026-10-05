---
kb_section: backend
type: service
ids: [BE-SVC-GSM]
service: GSM
repo: TZ-Tigo-SuperApp-GSM
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 13fe724
updated: 2026-10-05
confidence: partial
---

# Business rules — GSM

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-GSM-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
