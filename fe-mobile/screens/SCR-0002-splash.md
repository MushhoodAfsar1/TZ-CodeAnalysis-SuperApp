---
kb_section: fe-mobile
type: screen
ids: [SCR-0002]
feature: splash
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# SCR-0002 Splash (`SplashScreen`)

**Controller:** `SplashController` (`lib/ui/controllers/splash/splash_controller.dart`) · **Flow:** FLW-0002

App root. Not pushed by another auth screen.

## Calls

| Order | API | When | Fields read |
|---|---|---|---|
| 1 | API-0367 gateway `oauth2/token` | Cached gateway token missing or expired | `accessToken`, `expiresIn` stored as the gateway token. Not a session JWT. |
| 2 | API-0007 `requestPreLoginConfigs` | After remote config, when the cache or version misses | `responseData.result.isMoreEnable`, `responseData.result.isGuestModeEnabled`. Full body saved in preferences. No-internet callback still continues to redirect. |
| 3 | API-0318 `requestBoConfigurations` | Inside `redirectUserOnNextScreen` | `responseData` → `AppUtil.boResponse`. Path-only vs BE-API-CONFIG-392. |

Login, CheckAuth, and OTP are not called here.

## Navigation

| Condition | Destination |
|---|---|
| Maintenance or outage flags set | Alert only |
| `PreferenceKeys.userLoginDataNew` set and guest mode off | `LoginWidget` (SCR-0003) |
| Same and guest mode on | `HomeNewNavigationWidget` |
| Else | `WelcomeWidget` |

## Evidence

- `lib/ui/controllers/splash/splash_controller.dart` › `startApp`, `fetchAllConfigsBeforeAppStart`, `redirectUserOnNextScreen` @ `6328b7254`
- `lib/core/session_networking/session_network_manager.dart` › `requestGenerateGateWayToken`
