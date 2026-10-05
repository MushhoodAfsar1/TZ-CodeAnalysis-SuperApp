---
kb_section: backend
type: service
ids: [BE-SVC-NOTIF]
service: NOTIF
repo: TZ-Tigo-SuperApp-Notification
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: b7c98ec
updated: 2026-10-05
confidence: partial
---

# Errors — NOTIF

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-NOTIF-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-NOTIF-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
