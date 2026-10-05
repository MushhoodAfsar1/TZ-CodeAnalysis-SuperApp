---
kb_section: backend
type: overview
ids: [BE-OVR-SEC]
service: ALL
repo: multi
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: multi
updated: 2026-10-05
confidence: confirmed
---
# Security and crypto (mechanism only)

## Envelope
Mobile APIs accept `{ "payload": "<string>" }`. When config `isEncrypted` is `"true"`, `RequestSecurity.Receive<T>` decrypts the string to DTO `T` and stores it in `HttpContext.Items["modeldata"]`. Responses are wrapped with `RequestSecurity.Send`.

## Algorithm family
`System.Security.Cryptography.Aes` (CBC via `Aes.Create()` encryptor/decryptor), UTF-8 JSON, Base64 ciphertext. Key material from config keys `Encryption_Decryption_Key` and `IV` (values never recorded).

## Session JWT
HMAC-SHA256 JWT (`TokenKey`). Claims: `ClaimTypes.Name` = msisdn, `ClaimTypes.SerialNumber` = deviceid. Cache key shape: `device_session_{msisdn}_{deviceid}`. Expiry from `JwtExpiryMins` / `JwtRefreshExpiryMins` (seconds despite the name).

## IDENT
ASP.NET Identity lockout: `LockoutTimeSpan`, `MaxRetries`. LDAP bind for `loginwithad`. OTP emailed/SMS via `IOtpService`.

## Authz
IDENT `AuthorizationFilter`: skip list Login/LogOut/passwordchange/LoginWithOTP/ResendOtp/LoginWithAD; else Admin role or claim equal to `Controller:Action`.

## Session filter failure
WALLET-style `SessionValidationFilter` returns HTTP 410 Gone with `responseCode` = Gone and messages `No Token provided` / `Token Expired` / `Error in session validation`.
