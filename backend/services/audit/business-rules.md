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

# Business rules — AUDIT

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-AUDIT-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
