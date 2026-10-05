---
kb_section: backend
type: service
ids: [BE-SVC-MCHANGO]
service: MCHANGO
repo: TZ-Tigo-SuperApp-MChango
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 7c288ab
updated: 2026-10-05
confidence: partial
---

# Errors — MCHANGO

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-MCHANGO-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-MCHANGO-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
