---
kb_section: fe-mobile
type: screen
ids: [SCR-0019]
feature: billpayment
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# SCR-0019 Other-bill amount (`EnterAmountForPayBillWidget`)

**Controller:** `EnterAmountForPayBillController` · **Flow:** FLW-0008 · **API:** API-0034

## Entry

Other-bills list, search, or a selected category. The biller list itself is API-0012 (`requestGetBanksAndBillers`) on `OtherBillsPaymentController`. That list screen is not numbered here.

## Actions

| Action | Validation | API | Result |
|---|---|---|---|
| Type amount | At least `billPaymentMinAmount` (100). Above the cached wallet `mainBalance` shows an exceed message | — | Next |
| Next | Amount and reference present | API-0034 | Confirm when inquiry succeeds |

The inquiry body includes `descriptionText`, `consumerID`, `referenceID`, `sourceMSISDN`, `sourcePIN` (often empty on this screen), `terminalType`, `shortCode`, `amount` (currency and commas stripped), `targetRefNumber`, and `isBankTransfer`.

## Response branches

Success reads `responseData.fee`, `billPayer`, and `totalAmount`, then opens SCR-0020. Failure shows the inquiry error dialog.

Favorites add/remove on the bills list (API shared with other features) is not re-traced here.

## Evidence

- `lib/ui/controllers/billpayment/enter_amount_for_pay_bill_controller.dart` @ `6328b7254`
- `lib/ui/widgets/billpayment/enter_amount_for_pay_bill_widget.dart`
- `lib/models/network/bills/inquirry_reference_number_response_model.dart`
