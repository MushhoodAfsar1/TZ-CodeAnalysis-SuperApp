---
kb_section: backend
type: service
ids: [BE-SVC-MERSET]
service: MERSET
repo: TZ-Tigo-SuperApp-MerchantSettlementScheduler
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: d638213
updated: 2026-10-05
confidence: partial
---

# Errors — MERSET

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-MERSET-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-MERSET-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
