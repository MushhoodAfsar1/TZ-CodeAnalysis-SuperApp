---
kb_section: backend
type: service
ids: [BE-SVC-AUDIT]
service: AUDIT
repo: TZ-Tigo-SuperApp-AuditLogs
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: eb87819
updated: 2026-10-05
confidence: partial
---

# Errors — AUDIT

See also `overview/error-model.md`.

| ID | BE code | HTTP | Meaning | Raised in | APIs | Retryable |
|---|---|---|---|---|---|---|
| BE-ERR-AUDIT-001 | 500 | 500 | Unhandled exception | controller catch | all | depends |
| BE-ERR-AUDIT-002 | session | 410 | Invalid session | SessionValidationFilter | session-gated | no |
