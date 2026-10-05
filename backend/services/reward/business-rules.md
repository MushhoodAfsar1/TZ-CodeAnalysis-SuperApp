---
kb_section: backend
type: service
ids: [BE-SVC-REWARD]
service: REWARD
repo: TZ-Tigo-SuperApp-RewardReferral
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: b47cb93
updated: 2026-10-05
confidence: partial
---

# Business rules — REWARD

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-REWARD-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
