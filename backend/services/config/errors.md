---
kb_section: backend
type: service
ids: [BE-SVC-CONFIG]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: partial
---

# Errors — CONFIG

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-CONFIG-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-CONFIG-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
