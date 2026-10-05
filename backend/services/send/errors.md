---
kb_section: backend
type: service
ids: [BE-SVC-SEND]
service: SEND
repo: TZ-Tigo-SuperApp-SendMoney
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 599771b
updated: 2026-10-05
confidence: partial
---

# Errors — SEND

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-SEND-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-SEND-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
