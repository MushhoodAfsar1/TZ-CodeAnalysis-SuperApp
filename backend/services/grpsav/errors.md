---
kb_section: backend
type: service
ids: [BE-SVC-GRPSAV]
service: GRPSAV
repo: TZ-Tigo-SuperApp-GroupSaving
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: ed4ac20
updated: 2026-10-05
confidence: partial
---

# Errors — GRPSAV

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-GRPSAV-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-GRPSAV-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
