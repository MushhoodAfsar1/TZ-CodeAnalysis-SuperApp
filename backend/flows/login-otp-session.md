---
kb_section: backend
type: flow
ids: [BE-FLW-001]
service: ALL
repo: multi
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: multi
updated: 2026-10-05
confidence: confirmed
---
# BE-FLW-001 Login / OTP / session

## Mobile (customer)
1. SESS `POST /api/Account/auth` with `msisdn` + `deviceid` after ACCOUNT profile check (`CheckAuthenticationAsync`).
2. JWT access + refresh stored in Redis `device_session_{msisdn}_{deviceid}` and `tokens` table.
3. Subsequent feature APIs send `X-User-Session` + AES `payload`; `SessionValidationFilter` checks cache then DB.

## Portal (IDENT)
1. `POST /api/Account/login` or `loginwithad` (LDAP bind) → OTP via email/SMS.
2. `POST /api/Account/login2fa` completes login and issues portal JWT (header `X-User-Session`).
3. `AuthorizationFilter` enforces `Controller:Action` claims or Admin.

```mermaid
sequenceDiagram
  participant App
  participant SESS
  participant ACCOUNT
  participant Redis
  App->>SESS: POST /api/Account/auth
  SESS->>ACCOUNT: CheckAuthenticationAsync(msisdn)
  SESS->>Redis: device_session_{msisdn}_{deviceid}
  SESS-->>App: access + refresh JWT
```

Evidence: `TZ-Tigo-SuperApp-Session/.../AccountController.Auth`, `TZ-Tigo-SuperApp-Identity/.../AccountController.LoginWithAD`.
