---
kb_section: backend
type: service
ids: [BE-SVC-VCARD]
service: VCARD
repo: TZ-Tigo-SuperApp-VirtualCard
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: db358e6
updated: 2026-10-05
confidence: partial
---

# Errors — VCARD

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-VCARD-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-VCARD-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
