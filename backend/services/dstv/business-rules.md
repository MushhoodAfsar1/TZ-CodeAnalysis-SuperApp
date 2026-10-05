---
kb_section: backend
type: service
ids: [BE-SVC-DSTV]
service: DSTV
repo: TZ-Tigo-SuperApp-DigitalSubscription
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: fd31aa1
updated: 2026-10-05
confidence: partial
---

# Business rules — DSTV

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-DSTV-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
