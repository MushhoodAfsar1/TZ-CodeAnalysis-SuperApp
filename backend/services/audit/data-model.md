---
kb_section: backend
type: service
ids: [BE-SVC-AUDIT]
service: AUDIT
repo: TZ-Tigo-SuperApp-AuditLogs
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: eb87819
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-AUDIT data model

See EF DbContext in the service project. IDENT: `ApplicationUser` (Identity) + roles/claims. SESS: `Tokens` (msisdn, deviceid, access/refresh, expiries).

