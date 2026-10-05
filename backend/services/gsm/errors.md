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

# Errors — GSM

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-GSM-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-GSM-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
