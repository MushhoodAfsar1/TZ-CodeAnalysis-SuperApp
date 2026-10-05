---
kb_section: backend
type: service
ids: [BE-SVC-PORTAL]
service: PORTAL
repo: TZ-Tigo-SuperApp-WebPortal
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: bb69e15
updated: 2026-10-05
confidence: partial
---

# Errors — PORTAL

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-PORTAL-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-PORTAL-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
