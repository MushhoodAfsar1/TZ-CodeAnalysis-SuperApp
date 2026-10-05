---
kb_section: fe-mobile
type: screen
ids: [SCR-0006, SCR-0007, SCR-0008]
feature: registration_onboarding
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: partial
---

# SCR-0006–0008 Self-onboard and PIN

**Flow:** FLW-0003. Biometric and micro-business branches are not fully traced.

## SCR-0006 Account registration

**Widget:** `AccountRegistration` · **Controller:** `AccountRegistrationController` · **API:** API-0198 `checkNidaId` (`BE-API-ACCOUNT-012`, still path-only).

The widget compares `responseData.idValue` with the typed NIDA value, then opens verification.

## SCR-0007 Verification

**Widget:** `VerificationQuestion` · **Controller:** `VerificationAccountController`.

NIDA questions, then API-0200 / API-0201 (OTP V2, fe-only), then API-0202 `registerAccount`. Success opens the self-onboard PIN screen.

## SCR-0008 Set or change PIN

| Widget | Controller | API |
|---|---|---|
| `ChangePINSelfOnboardingWidget` | `ChangePinRegistrationController` | API-0073 `requestChangePin` |
| `PinChangerWidget` | `PinChangerWidgetController` | Local check: current PIN equals `PreferenceKeys.userMpKey`, length 4, then `SetNewPINWidget` |
| `SetNewPINWidget` | `SetNewPINWidgetController` | API-0073 when new and confirm match and both have length 4 |
| `ResetPinEnterNidaWidget` | `ResetBinEnterNidaWidgetController` | API-0075 `requestPinReset`, then SCR-0004 |
| `PinChangerSuccessWidget` | `PinChangerSuccessWidgetController` | API-0001 then the dashboard |

`AuthPinCodeFieldsForConfirmationController` only tracks completion against length 4. It does not call an API. API-0008 `requestCreateUserPIN` has no caller.

## Evidence

- `lib/ui/controllers/registration_onboarding/` @ `6328b7254`
- `lib/ui/controllers/pinchanger/set_new_pin_widget_controller.dart`
- `lib/ui/controllers/pinchanger/resetpin/reset_pin_enter_nida_widget_controller.dart`
