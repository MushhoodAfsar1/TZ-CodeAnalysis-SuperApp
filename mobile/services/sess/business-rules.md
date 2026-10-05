---
kb_section: mobile
type: service
ids: [FE-BR-SESS-001, FE-BR-SESS-002, FE-BR-SESS-003, FE-BR-SESS-004, FE-BR-SESS-005, FE-BR-SESS-006, FE-BR-SESS-007]
be_ids: [BE-BR-SESS-001, BE-ERR-SESS-002]
service: SESS
repo: TZ-Tigo-SuperApp-Mobile
repo_ref: main
repo_sha: 6328b7254
be_kb_ref: cursor/frontend-mobile-api-analysis-ad82
be_kb_sha: 2655b7a
updated: 2026-10-05
confidence: confirmed
---

# Business rules — SESS (mobile)

| FE-BR | Rule (business language) | Type | Enforced in FE (evidence) | BE-BR link | Alignment | APIs | Screens | Conf. |
|---|---|---|---|---|---|---|---|---|
| FE-BR-SESS-001 | The app refreshes the session only when the access JWT is already expired and the clock is inside the last 35 seconds before the refresh token expires (`diff > -35` and `diff < 0` seconds). A second call waits until the first callback returns (`refreshTokenCallCount`). Missing expiry or login time skips the call. | sequencing | `lib/ui/controllers/controller_commons/commons_functions.dart › CommonFunctions.checkAndCallRefreshLoginAuthToken` | — | fe-only | BE-API-SESS-002 | FE-SCR-001, app shell | confirmed |
| FE-BR-SESS-002 | When that refresh expiry time has already passed (`diff >= 0`), the app goes to login and does not call refresh. | sequencing | `CommonFunctions.checkAndCallRefreshLoginAuthToken` | — | fe-only | BE-API-SESS-002 | FE-SCR-001, app shell | confirmed |
| FE-BR-SESS-003 | After logout has started, the check returns immediately. An empty access token, or a token `JwtDecoder` cannot read, goes to login. If the user is not logged in, the login redirect returns without changing the screen (guest stays). | eligibility | `CommonFunctions.checkAndCallRefreshLoginAuthToken`, `CommonFunctions._handleInvalidToken`, `lib/core/app_manager/user_data_manager.dart › UserDataManager.redirectToLoginScreenOnRefreshTokenExpiry` | — | fe-only | BE-API-SESS-002 | FE-SCR-001, app shell | confirmed |
| FE-BR-SESS-004 | HTTP 410 on any call means the access session is no longer accepted. The app refreshes in the background and sends the original call again. The attempt counter resets on a new call and stops the loop once it has passed 2 on the same chain. The retry is always POST. | sequencing | `lib/core/network/manager/network_manager.dart › NetworkManager.callDioAPI`, `lib/core/network/manager/isolates_network_manager.dart › IsolateNetworkManager` | BE-BR-SESS-001 (session must be valid). BE-ERR-SESS-002 is the 410 the app reacts to. The cap of 2 is fe-only. | both | BE-API-SESS-002 | any in-flight call | confirmed |
| FE-BR-SESS-005 | HTTP 411 means the refresh token itself is no longer accepted. The logged-in user is sent to login. The original call is not retried. | security | `IsolateNetworkManager` (411 branch), `NetworkManager.callDioAPI`, `UserDataManager.redirectToLoginScreenOnRefreshTokenExpiry` | — | fe-only | BE-API-SESS-002 | any in-flight call | confirmed |
| FE-BR-SESS-006 | Pointer and resume checks run only when `UserDataManager.isLoggedIn` is true. | eligibility | `lib/main.dart › Listener`, `lib/ui/controllers/homepage/home_page_widget_controller.dart › HomePageWidgetController.onResumed` | — | fe-only | BE-API-SESS-002 | FE-SCR-001, app shell | confirmed |
| FE-BR-SESS-007 | When the app sends the user to login for an expired session, it replaces the navigation stack with `LoginWidget` and shows no dialog. `LocalizationKeys.sessionExpiredText` ("Your current session has expired. Login again to proceed.") exists and both alert call sites are commented out. | UX | `UserDataManager.redirectToLoginScreenOnRefreshTokenExpiry` | — | fe-only | BE-API-SESS-002 | login destination | confirmed |
