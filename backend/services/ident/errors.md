---
kb_section: backend
type: service
ids: [BE-SVC-IDENT]
service: IDENT
repo: TZ-Tigo-SuperApp-Identity
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: e7397b0
updated: 2026-10-05
confidence: partial
---

# Errors — IDENT

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-IDENT-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-IDENT-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
