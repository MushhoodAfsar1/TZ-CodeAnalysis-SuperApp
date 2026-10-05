---
kb_section: fe-mobile
type: screen
ids: [SCR-0004]
feature: otp
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# SCR-0004 OTP (`OTPSecondStepWidget`)

**Controller:** `OTPSecondStepWidgetController` · **Flow:** FLW-0002 · **APIs:** API-0005, API-0006 (`fe-only` V2 paths)

## Entry

`DeviceRegistrationHelper` from onboarding or login `UM-Lo-01`. Also security, self-care, and reset-PIN callers.

## Behaviour

`onReady` starts the timer and calls `requestGetOTP`. Verify runs when the typed or autofilled code reaches the platform max length. Resend is allowed after the timer (`otptimeout` from pre-login, else 60 seconds) and is blocked while `isOtpRequestInProgress`.

`otpType` is `deviceRegistration` when the cause is `userRegisteredButDeviceNotRegistered` or `deviceRegistrationFromLogin`. Otherwise it is omitted.

| Cause | After verify |
|---|---|
| `deviceRegistrationFromLogin` | `requestUserLogin` again with the pending PIN |
| Default device registration | Android: `PermissionInfoWidget` then login. iOS: login |
| `isResett` | `Get.back(result: true)` |
| `userAndDeviceBothNotRegistered`, `userRegisteredButMPinNotCreated` | Navigation is commented out |

Generate reads `responseData.isDebugNumber` for the debug keyboard only.

OTP max length is 20 on Android and 9 on iOS (BR-0010).

## Evidence

- `lib/ui/controllers/otp/otp_second_step_widget_controller.dart` @ `6328b7254`
- `lib/utils/app_util/app_util.dart` › `getOTPMaxLength`, `getOTPMaxIosLength`
