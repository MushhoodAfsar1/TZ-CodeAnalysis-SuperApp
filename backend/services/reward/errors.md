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

# Errors — REWARD

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-REWARD-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-REWARD-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
