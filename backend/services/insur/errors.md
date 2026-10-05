---
kb_section: backend
type: service
ids: [BE-SVC-INSUR]
service: INSUR
repo: TZ-Tigo-SuperApp-Insurrance
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 38747da
updated: 2026-10-05
confidence: partial
---

# Errors — INSUR

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-INSUR-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-INSUR-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
