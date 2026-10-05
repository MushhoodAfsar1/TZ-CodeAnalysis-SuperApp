---
kb_section: fe-mobile
type: overview
ids: [FE-SESSION]
feature: session-and-auth
fe_ref: main
fe_sha: 6328b7254
updated: 2026-10-05
confidence: partial
---
# Session and auth (inventory notes only)

Deep pass not done. These facts are only what the API methods themselves build. Controllers decide when they run.

| Step | API | Path | Encrypted | Notes |
|---|---|---|---|---|
| Gateway token | `SessionNetworkManager.requestGenerateGateWayToken` | `POST oauth2/token` | no | `grant_type` client_credentials. `scope` is a random request reference, not an OAuth scope list. Wrapper: `ApiManager.requestGenerateGateWayToken`. Seen from splash and `NetworkManager` |
| Check auth | `ApiManager.requestToCheckAuthV1` | `POST accounts/api/Profile/CheckAuthV2` | yes | The method name says V1; the constant is `requestCheckAuthV2`. Use-case `UseCaseTypes.checkAuthSuccess`. `userCaseName` registration |
| OTP request | `ApiManager.requestGetOTP` | `POST accounts/api/Otp/GenerateOtpV2` | yes | Optional `otpType`. **fe-only** — catalog has GenerateOtp / V1 / enc, not V2 |
| OTP verify | `ApiManager.requestVerifyOTP` | `POST accounts/api/Otp/VerifyOtpV2` | yes | Body includes `otp`. Same V2 gap |
| Login | `ApiManager.requestUserLogin` | `POST accounts/api/Profile/LoginProfile` | yes | `mpin`, `ismerchant=false`, `pushUpdateStatus`. Caller file: `common_api_functions.dart`. BE-API-ACCOUNT-002 path-only |
| Merchant login | `ApiManager.requestMerchantLogin` | same LoginProfile path | yes | `ismerchant` from the argument (default true) |
| Refresh | `ApiManager.requestRefreshLoginAuthToken` | `POST sessions/api/Account/refreshToken` | yes | Sends `accesstoken` and `refreshtoken` from `UserDataManager`. Invoked by wrapper `callRefreshLoginAuthToken`. BE-API-SESS-002 path-only |
| Create PIN | `ApiManager.requestCreateUserPIN` | `POST accounts/1.0.0/api/profiles/creatempin` | yes | `new_mpin`. No caller file found. fe-only |
| Pre-login config | `ApiManager.requestPreLoginConfigs` | `POST configuration/api/ConfigurationApp/get` | yes | BE-API-CONFIG-401 path-only |

Commented and unused: `requestToCheckAuth` (CheckAuth, not V2) is commented out. `UrlConstants.requestCheckAuth` is unused by a live call.

Open: which screen calls login vs check-auth vs OTP, and what response fields are stored on `UserDataManager`. That is the next deep pass.
