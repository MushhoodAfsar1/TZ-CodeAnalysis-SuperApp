---
kb_section: fe-mobile
type: screen
ids: [SCR-0023]
feature: tanzania_gift
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# SCR-0023 Gift history (`TanzaniaGiftMoneyWidget`)

**Controller:** `TanzaniaGiftMoneyWidgetController` · **Flow:** FLW-0009 · **API:** API-0096

## Entry

Gift money from the bottom nav, or `TanzaniaGiftNew` when the argument says it is not already from the bottom nav. `onReady` loads the top five only in the second case. The bottom-nav path calls `callOnReadyFunctionFromBottomNav`.

## Actions

| Action | Validation | API | Result |
|---|---|---|---|
| Open | — | API-0096 | Splits `responseData.receiverResult` and `senderResult` |
| Pick a person | — | — | Contact selection, then the theme flow |
| Open a past gift | — | — | `TanzaniaGiftOpenWidget` (display only, no API) |

Each history row reads `categoryid`, `themeid`, `transactionid`, `transferamount`, `transferto`, `transferfrom`, `transferdate`, `isdisplayed`, `agentName`, `message`, `imageurl`, `categoryurl`, `agentImage`.

Failure shows the gift top-five error dialog.

## Evidence

- `lib/ui/controllers/tanzania_gift/tanzania_gift_money/tanzania_gift_money_wiget_controller.dart` @ `6328b7254`
- `lib/ui/widgets/tanzania_gift/tanzania_gift_money/tanzania_gift_money_wiget.dart`
