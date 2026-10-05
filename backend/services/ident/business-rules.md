---
kb_section: backend
type: service
ids: [BE-SVC-IDENT]
service: IDENT
repo: TZ-Tigo-SuperApp-Identity
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: e7397b0
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-IDENT business rules

| ID | Rule (business language) | Type | Enforced where | Config key | APIs | Conf. |
|---|---|---|---|---|---|---|
| BE-BR-IDENT-001 | Portal actions require Admin role or claim `Controller:Action` except login/otp/logout/passwordchange | authz | AuthorizationFilter | — | IDENT account/menu/permission | confirmed |
| BE-BR-IDENT-002 | New portal users get role `NewUser` | identity | AccountController.register | — | BE-API-IDENT-001 | confirmed |
| BE-BR-IDENT-003 | Soft-deleted users can be reactivated on register | identity | AccountController.register | — | BE-API-IDENT-001 | confirmed |
| BE-BR-IDENT-004 | Inactive, deleted, or expiry-passed users cannot AD-login | eligibility | LoginWithAD | — | loginwithad | confirmed |
| BE-BR-IDENT-005 | ASP.NET Identity lockout uses MaxRetries and LockoutTimeSpan | security | AddIdentity | MaxRetries, LockoutTimeSpan | login | confirmed |

