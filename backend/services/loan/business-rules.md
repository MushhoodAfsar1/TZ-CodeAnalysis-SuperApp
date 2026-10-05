---
kb_section: backend
type: service
ids: [BE-SVC-LOAN]
service: LOAN
repo: TZ-Tigo-SuperApp-Loan
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 759a471
updated: 2026-10-05
confidence: partial
---

# Business rules — LOAN

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-LOAN-001 | Session JWT in `X-User-Session` must be valid and present in cache/DB | security | SessionValidationFilter | TokenKey | session-gated APIs | confirmed |
