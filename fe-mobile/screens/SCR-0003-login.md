---
kb_section: fe-mobile
type: screen
ids: [SCR-0003]
feature: login
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# SCR-0003 Login (`LoginWidget`)

**Controller:** `LoginWidgetController` (`lib/ui/controllers/login/login_widget_controller.dart`) · **Flow:** FLW-0002 · **API:** API-0001

There is no separate revamp login controller. Guest login uses the same `requestUserLogin` mixin.

## Entry

Splash when a session is cached and guest mode is off. Onboarding `UM-Lo-04`. OTP success (default and Android permission path). Refresh expiry and HTTP 411 (FLW-0001).

## Actions

| Action | Validation | API | Result |
|---|---|---|---|
| Type PIN | Length 4 (BR-0008) | — | Enables the button |
| Login or biometrics | PIN complete, or `PreferenceKeys.userMpKey` after hardware auth | API-0001 | See branches |
| PIN `0000` | — | OTP then optional `SetNewPINWidget` | Reset path |

`ismerchant` is false. `pushUpdateStatus` follows `isNewPushId`. `mpin` is the typed PIN or the biometric secret.

## Response branches

Success requires non-empty `responseData.accessCode`. `handleLoginResponse` stores `accessCode` (Bearer prefix) as the session token, `refreshToken`, `refreshTokenExpiryMinutes`, and `loggedInTime`. Merchant preference opens SCR-0001. Otherwise `NewBottomNavigationBarWidget`, unless a first-time biometric prompt shows.

| Code | Next |
|---|---|
| `UM-Lo-01` | Device-registration dialog, then SCR-0004 |
| `UM-Lo-16` | Device-limit dialog |
| Other failure | Error dialog, PIN cleared |

## Evidence

- `lib/ui/controllers/login/login_widget_controller.dart` › `callRequestUserLogin` @ `6328b7254`
- `lib/ui/controllers/controller_commons/common_api_functions.dart` › `requestUserLogin`
- `lib/ui/controllers/controller_commons/commons_functions.dart` › `handleLoginResponse`, `schedulePostLoginNavigation`
