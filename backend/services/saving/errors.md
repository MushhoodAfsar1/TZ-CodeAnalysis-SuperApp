---
kb_section: backend
type: service
ids: [BE-SVC-SAVING]
service: SAVING
repo: TZ-Tigo-SuperApp-Saving
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 2ca8791
updated: 2026-10-05
confidence: partial
---

# Errors — SAVING

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-SAVING-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-SAVING-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
