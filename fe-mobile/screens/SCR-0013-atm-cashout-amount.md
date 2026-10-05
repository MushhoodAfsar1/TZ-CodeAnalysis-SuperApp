---
kb_section: fe-mobile
type: screen
ids: [SCR-0013]
feature: atm_cashout
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# SCR-0013 ATM cash-out amount (`AtmCashoutEnterAmountWidget`)

**Controller:** `AtmCashoutEnterAmountWidgetController` · **Flow:** FLW-0006 · **API:** API-0158

## Entry

Dashboard ATM cash-out menu. `onReady` loads the bank list before the user types an amount.

## Actions

| Action | Validation | API | Result |
|---|---|---|---|
| Open | — | API-0158 | Dropdown from `responseData.ListOfATM` |
| Pick a bank | — | — | Stores `ID`, `BankName`, `MinAmount`, `MaxAmount`. Tiles are min, min × 20, and max |
| Type amount | Above max or below min shows an error. Limits stay `"0.0"` until a bank is picked, and those checks are skipped | — | Next stays enabled when the amount is non-empty and inside the limits |
| Next | Amount non-empty and not over/under the limits. A bank is not required when limits are still `"0.0"` | — | Opens SCR-0014 with `feeAmount` `"10.0"` (BR-0013). No fee call |

Failure of API-0158 shows the bank-list error dialog. An empty `ListOfATM` does not call the completion, so the dropdown stays empty.

## Evidence

- `lib/ui/controllers/atm_cashout/atm_cashout_enter_amount_widget_controller.dart` › `requestList` @ `6328b7254`
- `lib/ui/widgets/atm_cashout/atm_cashout_enter_amount_widget.dart` › bank `onChanged`, `getNextButtonContainer`
