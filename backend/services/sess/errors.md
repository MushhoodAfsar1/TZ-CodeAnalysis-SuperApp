---
kb_section: backend
type: service
ids: [BE-SVC-SESS]
service: SESS
repo: TZ-Tigo-SuperApp-Session
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 6f24061
updated: 2026-10-05
confidence: partial
---

# Errors — SESS

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-SESS-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-SESS-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
