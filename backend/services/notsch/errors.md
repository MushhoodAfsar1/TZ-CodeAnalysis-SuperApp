---
kb_section: backend
type: service
ids: [BE-SVC-NOTSCH]
service: NOTSCH
repo: TZ-Tigo-SuperApp-Notification-Scheduler
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 72838eb
updated: 2026-10-05
confidence: partial
---

# Errors — NOTSCH

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-NOTSCH-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-NOTSCH-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
