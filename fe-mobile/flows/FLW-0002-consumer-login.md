---
kb_section: fe-mobile
type: flow
ids: [FLW-0002]
feature: login
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# FLW-0002 Consumer login

**Screens:** SCR-0002 splash → welcome or login → SCR-0005 onboarding → SCR-0004 OTP → SCR-0003 login → consumer shell or SCR-0001 merchant home.

```mermaid
flowchart TD
  splash[SCR-0002 Splash]
  welcome[WelcomeWidget]
  guest[HomeNewNavigationWidget guest]
  onboard[SCR-0005 Onboarding CheckAuthV2]
  otp[SCR-0004 OTP V2]
  login[SCR-0003 Login LoginProfile]
  home[NewBottomNavigationBarWidget]
  merchant[SCR-0001 Merchant home]
  splash -->|cached session and guest off| login
  splash -->|cached session and guest on| guest
  splash -->|no cached session| welcome
  welcome -->|guest flag on| guest
  welcome -->|guest flag off| onboard
  onboard -->|UM-Lo-04| login
  onboard -->|UM-Lo-01| otp
  onboard -->|UM-Lo-12 and self-onboard allowed| reg[FLW-0003]
  otp -->|device registered| login
  login -->|accessCode stored and not merchant| home
  login -->|merchant preference| merchant
  login -->|UM-Lo-01| otp
```

Gateway token (API-0367) and pre-login config (API-0007) run on splash before any of these branches. They are not session JWTs.

PIN length is 4 (BR-0008). Login sends `mpin` and `msisdn` even though the published `LoginProfileRequest` omits both (GAP-0108).

## Evidence

- `lib/ui/controllers/splash/splash_controller.dart` › `redirectUserOnNextScreen`
- `lib/ui/widgets/welcome/welcome_widget.dart`
- `lib/ui/controllers/onboarding/onboarding_screen_controller.dart` › `handleCheckAuthResponse`
- `lib/ui/controllers/otp/otp_second_step_widget_controller.dart`
- `lib/ui/controllers/controller_commons/common_api_functions.dart` › `requestUserLogin`
- `lib/ui/controllers/controller_commons/commons_functions.dart` › `handleLoginResponse`
