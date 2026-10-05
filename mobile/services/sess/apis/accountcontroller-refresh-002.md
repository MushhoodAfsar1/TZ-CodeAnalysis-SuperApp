---
kb_section: mobile
type: api-usage
ids: [FE-API-SESS-002]
be_ids: [BE-API-SESS-002]
service: SESS
repo: TZ-Tigo-SuperApp-Mobile
repo_ref: main
repo_sha: 6328b7254
be_kb_ref: cursor/frontend-mobile-api-analysis-ad82
be_kb_sha: 2655b7a
updated: 2026-10-05
confidence: confirmed
---

# FE-API-SESS-002 AccountController.Refresh — mobile usage
**BE contract:** [../../../../backend/services/sess/apis/accountcontroller-refresh-002.md](../../../../backend/services/sess/apis/accountcontroller-refresh-002.md) (BE-API-SESS-002)
**Match status:** fe-used · **Conf.:** confirmed

## Match evidence

| BE public_path | FE endpoint const → resolved path | ApiManager method | Use-case | Encrypted (mechanism) | Search used |
|---|---|---|---|---|---|
| POST `/api/Account/refreshToken` | `UrlConstants.requestRefreshLoginAuthToken` → `sessions/api/Account/refreshToken` (host omitted; base key `UrlConstants.baseURL`) | `ApiManager.requestRefreshLoginAuthToken`, called only through `ApiManager.callRefreshLoginAuthToken` | none (`useCaseType` unset, `userCaseName` absent) | yes. Whole decrypted JSON is AES-wrapped in `payload` via `CryptoUtil`. `NetworkResponseKeysConstants.isEncryptionDone` is true. | `refreshToken` and `sessions/api` in `lib/core/network/` |

## Call sites

| # | Screen (FE-SCR) | Controller.method | Trigger | Condition(s) | Order / parallel | Fg/Bg |
|---|---|---|---|---|---|---|
| 1 | FE-SCR-001 Merchant home | `HomePageWidgetController.onResumed` → `CommonFunctions.checkAndCallRefreshLoginAuthToken` | App resume | C1–C6 | alone | Bg (`onForeground: false`) |
| 2 | App shell (no screen ID) | `main.dart` Listener → `CommonFunctions.checkAndCallRefreshLoginAuthToken` | Pointer down, move, or up | C1–C6 | alone; three gestures share one counter | Bg |
| 3 | Any screen with an in-flight API | `NetworkManager.callDioAPI` | HTTP 410 from the isolate | C7 | refresh, then the original call | Bg (`isRetryFromTokenRefresh: true`) |

`requestRefreshLoginAuthToken` has no other callers.

## Conditions & branches

- C1: The user is logged in. Otherwise the pointer and resume hooks return. — `main.dart` Listener, `HomePageWidgetController.onResumed` — skip.
- C2: Logout is already in progress (`isLogoutPerformed`). — `CommonFunctions.checkAndCallRefreshLoginAuthToken` — skip.
- C3: The stored access token is null or empty. — same method — go to login (`_handleInvalidToken`). No refresh call.
- C4: Refresh expiry minutes or `loggedInTime` is missing. — same method — skip.
- C5: `JwtDecoder.isExpired` throws. — same method — go to login. No refresh call.
- C6: The access JWT is expired and now is inside the last 35 seconds before refresh expiry, and no refresh callback is still the first in-flight call (`refreshTokenCallCount == 1` after increment). — same method — call refresh. If refresh expiry has already passed, go to login and do not call. If the JWT is still valid, do nothing.
- C7: An API response status is HTTP 410, and `isRefreshTokenCalledNumberOfTimes` is still 2 or less after increment. The counter resets to 0 when `callDioAPI` starts a call that is not itself a refresh retry. — `NetworkManager.callDioAPI` — call refresh, then repeat the original request on success. Past 2, complete the original call as a failure.
- C8: The refresh response status is HTTP 411. — `IsolateNetworkManager` and `NetworkManager.callDioAPI` — send the logged-in user to `LoginWidget`.

The proactive callback resets `refreshTokenCallCount` on both success and failure. A failed proactive refresh leaves the user on the current screen until C6's expiry branch or a later 410.

## Request: FE vs BE DTO

Wire body is `{ "payload": "<ciphertext>" }`. The table is the decrypted JSON inside that ciphertext. The backend contract lists `accesstoken` twice; the app sends it once.

| BE field | BE type / req. | Sent by FE? | FE source | FE format/validation | Note |
|---|---|---|---|---|---|
| `payload` | string, required on the wire | Y | `CryptoUtil.encrypt` of the JSON below | AES ciphertext | Envelope only. |
| `requestingOrganisationTransactionReference` | string, optional | Y | `DateTimeUtil.getCurrentDateTimeAsRandomString` | random date-time string | Not the common-body helper. |
| `iPInfo` | string, optional | N | — | — | FE-GAP-001 |
| `geoCode` | string, optional | N | — | — | FE-GAP-001 |
| `useCaseName` | string, optional | N | — | — | FE-GAP-001 |
| `channel` | string, optional | N | — | — | FE-GAP-001 |
| `appVersion` | string, optional | N | — | — | FE-GAP-001 |
| `languageCode` | string, optional | N | — | — | FE-GAP-001 |
| `deviceId` | string, optional | N | — | — | FE-GAP-001 |
| `deviceMaker` | string, optional | N | — | — | FE-GAP-001 |
| `oS` | string, optional | N | — | — | FE-GAP-001 |
| `accesstoken` | string, optional | Y | `UserDataManager.authTokenForCurrentlyLoggedInUser` | Includes the `Bearer ` prefix saved at login (`accessCode`) or by the previous refresh | FE-GAP-005 |
| `msisdn` | string, optional | N | — | — | FE-GAP-001 |
| `refreshtoken` | string, optional | Y | `UserDataManager.refreshAuthTokenForCurrentlyLoggedInUser` | Stored without a `Bearer ` prefix. Login field `refreshToken`, or the previous refresh `responseData.refreshtoken`. | |

Headers the app attaches (`NetworkManagerUtils.getRequestDefaultHeaders`):

| Header | Sent | Source |
|---|---|---|
| `Content-type` / `Accept` | Y | constants `application/json` |
| `isGuestModeEnabled` | Y | `AppUtil.isGuestModeEnabled` as a string |
| `X-Key-Version` | Y | constant `2` |
| `Authorization` | Y when a gateway token is stored | `UserDataManager.gateWayAuthTokenForCurrentlyLoggedInUser` |
| `X-User-Session` | Y when an access token is stored | same value as body `accesstoken` (may already be expired) |

The backend contract names `X-User-Session` and `Content-Type`. The other headers are extra on the wire.

## Response: BE fields vs FE consumption

The isolate treats a non-empty decrypted body on an HTTP status other than 403, 404, 410, 411, 422, and 401 as `isSuccess == true`. `callRefreshLoginAuthToken` then requires `responseData.accesstoken` to be non-empty. Envelope `success` and `responseCode` are parsed and not read.

| BE field | Read by FE? | Used for |
|---|---|---|
| `success` | N (parsed by `ResponseFields`, unused here) | — |
| `responseCode` | N (parsed, unused here) | — |
| `transactionStatus` | N (parsed, unused here) | — |
| `errorDescription` | N (parsed, unused here) | — |
| `appVersionInfo` | N | Not a field on `RefreshTokenResponseModel`. |
| `responseData` | Y | Must be present with a non-empty `accesstoken` or the callback returns false. |
| `responseData.accesstoken` | Y | Stored as `Bearer <jwt>` in `UserDataManager.authTokenForCurrentlyLoggedInUser`. Next calls send it as `X-User-Session`. Not in the BE contract (FE-GAP-002). |
| `responseData.refreshtoken` | Y | Stored in `refreshAuthTokenForCurrentlyLoggedInUser` (empty string if absent). Not in the BE contract. |
| `responseData.refreshTokenExpiryMinutes` | Y | Stored in `refreshAuthTokenExpiryInMinutes`. Drives FE-BR-SESS-001. Not in the BE contract. |
| `responseData.accesstokenexpirein` | N | Parsed onto the model, never read. |
| `responseData.refreshtokenexpirein` | N | Parsed. The write into `refreshAuthTokenExpiryTime` is commented out. |

## Error handling vs BE

| BE code / HTTP / BE-ERR | FE handling | Next step | Handled? |
|---|---|---|---|
| HTTP 500 / BE-ERR-SESS-001 | A non-empty body still arrives as `isSuccess` true. The handler then looks only at `responseData.accesstoken`. An empty body or a thrown decrypt completes false. | Proactive path: stay on the screen. 410-retry path: original call fails (`ResponseCompletionStatus.completedWithErrorOnNetworkLayer`, callback code 9999). No `errorDescription` dialog on this call. | partial |
| HTTP 410 / BE-ERR-SESS-002 | 410 is the trigger that starts this refresh (C7). If this refresh call itself returns 410, the same loop runs until the cap of 2. | Then the original caller gets a failure completion. | partial |
| Mapped `responseCode` with HTTP 200/400/201 | No branch on `responseCode` or `errorDescription`. | Tokens update only when `accesstoken` is non-empty. | no (FE-GAP-004) |
| HTTP 411 (not in BE-ERR-SESS) | Isolate notifies the main isolate. Logged-in user goes to `LoginWidget` with no dialog (`LocalizationKeys.sessionExpiredText` is unused). | `Get.offAll(LoginWidget)`. Guest (`isLoggedIn` false) stays. | FE handles; BE list silent (FE-GAP-003) |
| No internet (`ResponseCompletionStatus.noInternetConnection`) | Callback false before parsing. | Proactive path stays. 410-retry path fails the original call. | yes, local |

## Business rules

| FE-BR | Rule | BE-BR | Alignment |
|---|---|---|---|
| FE-BR-SESS-001 | 35-second window | — | fe-only |
| FE-BR-SESS-002 | Past expiry goes to login | — | fe-only |
| FE-BR-SESS-003 | Logout, empty token, bad JWT, guest | — | fe-only |
| FE-BR-SESS-004 | HTTP 410 refresh then retry, max 2 | BE-BR-SESS-001 | both |
| FE-BR-SESS-005 | HTTP 411 goes to login | — | fe-only |
| FE-BR-SESS-006 | Logged-in only | — | fe-only |
| FE-BR-SESS-007 | No session-expired dialog | — | fe-only |

## Other logic & side effects

- On success the app sets `loggedInTime` to `DateTime.now()` so the next window is measured from this refresh, and copies `refreshTokenExpiryMinutes` from the body.
- Tokens live in memory on `UserDataManager`. This call does not write them to preferences.
- No Firebase event on this call. Login success is a different event, on the account login response.
- Foreground loader is off. The keyboard-hide in `callDioAPI` still runs.
- After a successful 410 recovery the original request is repeated as POST with `isEncryptionDone` forced true and `onForeground` false, using a fresh `getRequestDefaultHeaders()` so `X-User-Session` is the new token.
- Debug builds may record the 410 response in the in-app HTTP inspector before refresh. That path is debug-only.

## Gaps

- FE-GAP-001 optional DTO fields omitted.
- FE-GAP-002 `responseData` token fields missing from the BE contract.
- FE-GAP-003 HTTP 411 handled, not listed on the BE service.
- FE-GAP-004 envelope status fields unused.
- FE-GAP-005 `accesstoken` sent with a `Bearer ` prefix.

Detail: [../../../gaps/fe-be-gaps.md](../../../gaps/fe-be-gaps.md).

## Evidence

- `lib/core/network/constants/network_constants.dart › UrlConstants.requestRefreshLoginAuthToken` @ `6328b7254`
- `lib/core/network/manager/api_ manager.dart › ApiManager.requestRefreshLoginAuthToken`
- `lib/core/network/manager/api_ manager.dart › ApiManager.callRefreshLoginAuthToken`
- `lib/ui/controllers/controller_commons/commons_functions.dart › CommonFunctions.checkAndCallRefreshLoginAuthToken`
- `lib/ui/controllers/homepage/home_page_widget_controller.dart › HomePageWidgetController.onResumed`
- `lib/main.dart` Listener (`onPointerDown` / `onPointerMove` / `onPointerUp`)
- `lib/core/network/manager/network_manager.dart › NetworkManager.callDioAPI`
- `lib/core/network/manager/isolates_network_manager.dart` HTTP 410 and 411 branches
- `lib/models/network/gatewaysession/refresh_token_response_model.dart › ResponseDataRefreshToken`
- `lib/core/app_manager/user_data_manager.dart › UserDataManager.redirectToLoginScreenOnRefreshTokenExpiry`

## Open questions

- Does the session service strip a leading `Bearer ` from `accesstoken` (`Replace` is named in the BE contract and the replacement text is not)?
- Are `refreshTokenExpiryMinutes`, `accesstokenexpirein`, and `refreshtokenexpirein` part of the real `responseData`?
- The retry after 410 always uses POST. GET calls that return 410 would be repeated as POST. Left for the architecture pass.
