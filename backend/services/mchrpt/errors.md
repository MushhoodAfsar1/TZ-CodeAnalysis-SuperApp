---
kb_section: backend
type: service
ids: [BE-SVC-MCHRPT]
service: MCHRPT
repo: TZ-Tigo-SuperApp-MChangoReportScheduler
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 34ba77f
updated: 2026-10-05
confidence: partial
---

# Errors — MCHRPT

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-MCHRPT-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-MCHRPT-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
