---
kb_section: backend
type: service
ids: [BE-SVC-STOCK]
service: STOCK
repo: TZ-Tigo-SuperApp-Stock
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 10f0a62
updated: 2026-10-05
confidence: partial
---

# Errors — STOCK

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-STOCK-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-STOCK-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
