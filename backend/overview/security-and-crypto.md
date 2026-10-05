---
kb_section: backend
type: overview
ids: [BE-OV-SEC]
service: ALL
repo: multi
repo_ref: checked-out
repo_sha: multi
updated: 2026-10-05
confidence: confirmed
---

# Security and crypto (mechanism only)

## Transport envelope
Most feature APIs wrap the JSON DTO in `payload`. When config `is_encrypted` (or `isEncrypted` in Wallet/GSM/Reward) is `"true"`:
- Decrypt: `RequestSecurity.Receive<T>` / `Encryption.Receive` — **AES CBC** via `Aes.Create()` + `CryptoStream`.
- Encrypt: whole **response object** JSON, not field-level.
- Filter class: `EncryptionProviderFilter<TEntity>` (typo `EncriptionProviderFilter` in Wallet/GSM/Reward).
- Binding: decrypted instance stored in `HttpContext.Items["modeldata"]`; action parameter remains `RequestModel`.

MChango: `EncryptionMiddleware` replaces request/response streams (section `EncryptionSecret`, flag `EnableEncryption`). USSD has a separate key/IV pair (names only).

Identity portal APIs are **not** payload-encrypted; they use JWT Bearer.

## Session
- Issued by SESS `POST /api/Account/auth` (`TokenDto`: msisdn, deviceid) — HMAC-SHA256 JWT claims Name=msisdn, SerialNumber=deviceid. Cache key shape `device_session_{msisdn}_{deviceid}`.
- Validated **locally** in each service (`SessionValidationFilter`): parse JWT with `TokenKey`, then Redis then Account `tokens` table. **Does not HTTP-call SESS** on each request.
- ACCOUNT `SessionManagement.EstablishSession` is the only `SMM` client (`Session:Configuration` + `api/Account/auth`).

## Config key names (no values)
`is_encrypted`, `isEncrypted`, `Encryption_Decryption_Key`, `IV`, `Encryption_Decryption_Key_V2`, encryption-secret section names, `TokenKey`, `JwtExpiryMins`, `JwtRefreshExpiryMins`, `Origins`, `RedisURL`.

Identity: `AddJwtBearer`, token from `X-User-Session`; `AuthorizationFilter` enforces `Controller:Action` claims (admin bypass).
