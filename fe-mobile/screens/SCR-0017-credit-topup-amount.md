---
kb_section: fe-mobile
type: screen
ids: [SCR-0017]
feature: airtimetopups
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# SCR-0017 Credit top-up amount (`MobileTopupWidget`)

**Controller:** `MobileTopupWidgetController` · **Flow:** FLW-0007 · **API:** none

## Entry

Airtime credit for self or another operator. `setContactNo` stores the receiver, the other-operator flag, and that operator's min and max.

## Actions

| Action | Validation | API | Result |
|---|---|---|---|
| Type amount | Self: pre-login `airtimeMinLimit` / `airtimeMaxLimit`, falling back to 100 and 10000. Other: the min and max passed in | — | Enables next (BR-0015) |
| Next | Amount inside the range | — | Opens SCR-0018 with `isOther` |

No HTTP call on this screen.

## Evidence

- `lib/ui/controllers/airtimetopups/credit_telma/mobile_top_up_widget_controller.dart` @ `6328b7254`
- `lib/ui/widgets/airtimetopups/credit_telma/mobile_topup_widget.dart` › `Get.to(MobileTopUPConfirmationWidget)`
- `lib/utils/constants/app_constants.dart` › `mobileTopUpMinAmount`, `mobileTopUpMaxAmount`
