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

# Errors — DSTV

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-DSTV-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-DSTV-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
