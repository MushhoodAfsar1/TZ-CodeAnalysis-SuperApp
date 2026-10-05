---
kb_section: backend
type: service
ids: [BE-SVC-ACCOUNT]
service: ACCOUNT
repo: TZ-Tigo-SuperApp-Account
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 5c549d6
updated: 2026-10-05
confidence: partial
---

# Errors — ACCOUNT

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-ACCOUNT-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-ACCOUNT-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
