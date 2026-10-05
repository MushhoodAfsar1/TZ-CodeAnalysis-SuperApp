---
kb_section: backend
type: overview
ids: [BE-OVR-PIPE]
service: ALL
repo: multi
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: multi
updated: 2026-10-05
confidence: confirmed
---
# Request pipeline

Typical **mobile feature** request (WALLET, SEND, ACCOUNT, …):

```mermaid
sequenceDiagram
  participant App
  participant Enc as EncryptionProviderFilter
  participant Sess as SessionValidationFilter
  participant Ctrl as Controller
  participant Svc as Service
  App->>Enc: POST JSON { payload: "<base64 AES>" }
  Enc->>Enc: AES decrypt if isEncrypted=true
  Enc->>Sess: HttpContext.Items["modeldata"]
  Note over App,Sess: Header X-User-Session
  Sess->>Sess: JWT claims msisdn + deviceid
  Sess->>Sess: Redis device_session_{msisdn}_{deviceid}
  alt cache miss or token mismatch
    Sess->>Sess: tokens table fallback
  end
  Sess->>Ctrl: action
  Ctrl->>Svc: decrypted DTO
  Svc-->>Ctrl: result object
  Ctrl-->>Enc: ObjectResult
  Enc-->>App: AES ciphertext if isEncrypted=true
```

**IDENT (portal):** `[Authorize(JwtBearer)]` + `AuthorizationFilter` (claim `Controller:Action` or role Admin). Login/OTP/AD/logout/passwordchange are AllowAnonymous bypasses in the filter. Token is read from header `X-User-Session` in JwtBearer `OnMessageReceived`.

**SESS:** `POST /api/Account/auth` issues access+refresh JWT; `POST /api/Account/refreshToken` uses encryption filter + validates stored refresh token. HTTP **411** is used as invalid-token status on refresh.

Config flags (names only): `isEncrypted` (most services) vs `is_encrypted` (IDENT filter).
