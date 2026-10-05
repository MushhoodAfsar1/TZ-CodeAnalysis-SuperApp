---
kb_section: backend
type: service
ids: [BE-SVC-LOAN]
service: LOAN
repo: TZ-Tigo-SuperApp-Loan
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 759a471
updated: 2026-10-05
confidence: partial
---

# Errors — LOAN

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-LOAN-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-LOAN-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
