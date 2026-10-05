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

# Business rules — MCHRPT

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-MCHRPT-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
