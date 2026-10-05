---
kb_section: fe-mobile
type: overview
ids: [FE-NAV]
feature: ALL
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: partial
---
# Navigation map

Entry is `lib/main.dart`. Auth and the two money journeys below are traced. Other GetX routes are not.

## Auth

`SplashScreen` → `WelcomeWidget` or `LoginWidget` or guest `HomeNewNavigationWidget`.

`WelcomeWidget` → `OnBoardingScreenWidget` (guest off) or guest home (guest on).

`OnBoardingScreenWidget` → `LoginWidget` (`UM-Lo-04`), `OTPSecondStepWidget` (`UM-Lo-01`), or `AccountRegistration` / `DiasStepperWidget` (`UM-Lo-12`).

`OTPSecondStepWidget` → `LoginWidget` (or Android `PermissionInfoWidget` first).

`LoginWidget` → `NewBottomNavigationBarWidget` (consumer) or `HomePageWidget` (merchant).

Refresh expiry and HTTP 411 replace the stack with `LoginWidget`.

## Money

Dashboard Mixx transfer → contact pick → `SendMoneyEnterAmountWidget` → `SendMoneyConfirmationWidget` → `ReceiptScrollWidget`.

Cash-out icon → recents → `CashPointEnterAmountWidget` → `CashPointConfirmationWidget` → `OlderReceiptScrollWidget`.

Screen IDs: [../catalog/screen-catalog.md](../catalog/screen-catalog.md).
