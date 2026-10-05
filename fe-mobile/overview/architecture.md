---
kb_section: fe-mobile
type: overview
ids: [FE-ARCH]
feature: ALL
fe_ref: main
fe_sha: 6328b7254
updated: 2026-10-05
confidence: confirmed
---
# FE architecture (network)

Verified at `main` @ `6328b7254`.

| Concern | Where |
|---|---|
| Call chain | Widget → GetxController → `ApiManager` static method → `NetworkManager.callDioAPI` → completion `(String response, bool isSuccess, ResponseCompletionStatus)` |
| API methods | `lib/core/network/manager/api_ manager.dart` › `ApiManager` (the filename contains a space) |
| Gateway token | `lib/core/session_networking/session_network_manager.dart` › `SessionNetworkManager.requestGenerateGateWayToken`. `ApiManager.requestGenerateGateWayToken` only delegates to it |
| Token refresh wrapper | `ApiManager.callRefreshLoginAuthToken` delegates to `ApiManager.requestRefreshLoginAuthToken` |
| Endpoint constants | `lib/core/network/constants/network_constants.dart` › `UrlConstants` (base host comes from theme / `UserDataManager`; only the path is recorded) |
| HTTP verbs | `RequestMethodConstants.post` / `.get` in the same constants file |
| Common body | `lib/core/network/manager/network_manager.utils.dart` › `NetworkManagerUtils.getCommonJSONRequestBody` |
| Use-case enum | `lib/utils/constants/app_enums.dart` › `UseCaseTypes` |
| Use-case name | `lib/utils/constants/use_case_constants.dart` › `UseCaseNameConstants` (some calls pass a string literal instead) |
| Encryption | `lib/utils/crypto_util/crypto_util.dart` › `CryptoUtil`. Almost every call encrypts the JSON and sends `{payload: ciphertext}`. `NetworkResponseKeysConstants.isEncryptionDone` is `true`. The gateway token call is not encrypted |
| Session state | `lib/core/app_manager/user_data_manager.dart` › `UserDataManager`; `app_data_manager.dart` › `AppDataManager`; `lib/core/preferences/preferences_manager.dart` › `PreferencesManager` |
| Controllers | Legacy `lib/ui/controllers/{feature}/`. Revamp `lib/ui/new_ui_revamp/{feature}/` |
| Screens | Legacy `lib/ui/widgets/`. Revamp widgets live under each revamp feature |
| Entry | `lib/main.dart` |
| Other HTTP | `lib/utils/app_util/app_util.dart` references `Dio` directly (2 hits). Not catalogued as `API-` until traced |

Timeouts default from pre-login config (`apitimeout`, else 60 seconds) in `RequestTimeoutConstants`. Individual calls can override `connectTimeout` / `receiveTimeOut` / `sendTimeout`. `onForeground: true` shows the global loader; `false` runs in the background. The flag is usually passed through from the controller, so foreground vs background is a call-site decision.

`getCommonJSONRequestBody` always writes `pushId`. The `isPushIdRequired` argument does not change the map. When `isGeoCodeRequired` is true and device coordinates are empty, `geoCode` is a fixed fallback pair (the pair is not stored in this KB).
