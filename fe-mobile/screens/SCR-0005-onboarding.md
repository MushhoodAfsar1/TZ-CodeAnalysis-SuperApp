---
kb_section: fe-mobile
type: screen
ids: [SCR-0005]
feature: onboarding
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# SCR-0005 Onboarding (`OnBoardingScreenWidget`)

**Controller:** `OnBoardingScreenController` · **Flow:** FLW-0002 · **API:** API-0004

## Entry

`WelcomeWidget` Continue when guest mode is off. Also guest sign-up sheets and some registration failure returns.

## Action

Next is enabled when the number length is at least 9 and `AppUtil.isMSISDNFieldValidWithPrefix`. The controller builds `fullNumber` with the country code and calls `requestToCheckAuthV1` (CheckAuthV2).

| `responseCode` | Next |
|---|---|
| `UM-Lo-04` | SCR-0003 with `isNewPushId: true` |
| `UM-Lo-01` | Save `primaryNumber`, device dialog, SCR-0004 |
| `UM-Lo-12` | If this app version is in `isAllowUserToSelfOnBoard`, domestic `AccountRegistration` (FLW-0003) or foreign `DiasStepperWidget`. Else an error alert. |
| `UM-Lo-16` | Device-limit dialog |
| Other | Generic error. No separate blocked-user branch in this handler. |

## Evidence

- `lib/ui/controllers/onboarding/onboarding_screen_controller.dart` › `requestCheckAuth`, `handleCheckAuthResponse` @ `6328b7254`
- `lib/ui/widgets/onboarding/onboarding_screen_widget.dart`
