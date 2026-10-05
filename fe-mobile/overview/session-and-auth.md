---
kb_section: fe-mobile
type: overview
ids: [FE-SESSION]
feature: session-and-auth
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---
# Session and auth

Traced at FE `6328b7254` against backend `0c13cc4`. Journey: [../flows/FLW-0002-consumer-login.md](../flows/FLW-0002-consumer-login.md). Refresh: [../flows/FLW-0001-session-refresh.md](../flows/FLW-0001-session-refresh.md). Field diff: [../contracts/session-auth-money.md](../contracts/session-auth-money.md).

| Step | API | Path | Match | Stored |
|---|---|---|---|---|
| Gateway token | API-0367 | `POST oauth2/token` | fe-only (not SESS-001) | Gateway `accessToken`, `expiresIn` |
| Pre-login config | API-0007 | `POST configuration/api/ConfigurationApp/get` | path-only BE-API-CONFIG-401 | `isGuestModeEnabled`, `isMoreEnable` |
| Check auth | API-0004 | `POST accounts/api/Profile/CheckAuthV2` | contract-mismatch BE-API-ACCOUNT-011 | Branches on `UM-Lo-01/04/12/16` |
| OTP | API-0005, API-0006 | `GenerateOtpV2`, `VerifyOtpV2` | fe-only | Device registration, then login |
| Login | API-0001 | `POST accounts/api/Profile/LoginProfile` | contract-mismatch BE-API-ACCOUNT-002 | `accessCode` as session JWT, `refreshToken`, expiry minutes |
| Refresh | API-0003 | `POST sessions/api/Account/refreshToken` | contract-mismatch BE-API-SESS-002 | Replaces the same three values |

The session JWT is the login `accessCode`, not a response from `POST /api/Account/auth`.
