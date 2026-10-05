---
kb_section: backend
type: service
ids: [BE-SVC-EXPENSE]
service: EXPENSE
repo: TZ-Tigo-SuperApp-Expense
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: e821ac9
updated: 2026-10-05
confidence: partial
---

# Errors — EXPENSE

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-EXPENSE-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-EXPENSE-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
