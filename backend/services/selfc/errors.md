---
kb_section: backend
type: service
ids: [BE-SVC-SELFC]
service: SELFC
repo: TZ-Tigo-SuperApp-SelfCare
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: a0aeca8
updated: 2026-10-05
confidence: partial
---

# Errors — SELFC

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-SELFC-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-SELFC-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
