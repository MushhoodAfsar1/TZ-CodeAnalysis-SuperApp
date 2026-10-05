---
kb_section: backend
type: service
ids: [BE-SVC-MERCH]
service: MERCH
repo: TZ-Tigo-SuperApp-Merchant
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 2367767
updated: 2026-10-05
confidence: partial
---

# Errors — MERCH

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-MERCH-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-MERCH-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
