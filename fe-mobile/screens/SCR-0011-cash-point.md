---
kb_section: fe-mobile
type: screen
ids: [SCR-0011, SCR-0012]
feature: cash_point
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# SCR-0011–0012 Cash point

**Flow:** FLW-0005

## SCR-0011 Amount

**Widget:** `CashPointEnterAmountWidget` · **Controller:** `CashPointEnterAmountWidgetController`

Entry from recents/favourites for `UseCaseTypes.cashOutAgent`. Amount must sit between `cashOutMinAmount` and `cashOutMaxAmount`. Lookup:

| Account | API |
|---|---|
| Consumer | API-0039 `requestCashOutfee` |
| Merchant | API-0040 |
| Mchango | `cashoutFeeMchnago` |

Consumer UI reads `responseData.fee` and `responseData.additionalResults[1].parameterValue` (index 1 is fixed). Merchant UI reads `responseData.name` and `responseData.fee`.

## SCR-0012 Confirm

**Widget:** `CashPointConfirmationWidget` · **Controller:** `CashPointConfirmationWidgetController`

PIN complete, then `initiateCashOut` with the same consumer / merchant / Mchango split. Consumer payment is API-0041. Receipt is `OlderReceiptScrollWidget` using `responseData.transactionId`. Overdraft retries with `overDraftBrandId`.

## Evidence

- `lib/ui/controllers/cash_point/cash_point_enter_amount_widget_controller.dart` › `cashOutLookUp` @ `6328b7254`
- `lib/ui/controllers/cash_point/cash_point_confirmation_widget_controller.dart` › `initiateCashOut`
