---
kb_section: fe-mobile
type: screen
ids: [SCR-0009, SCR-0010]
feature: sendmoney
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: partial
---

# SCR-0009–0010 Send money amount and confirm

**Flow:** FLW-0004 · **APIs:** API-0013, API-0014

## SCR-0009 Amount

**Widget:** `SendMoneyEnterAmountWidget` · **Controller:** `SendMoneyEnterAmountController`

Reached after contact pick, which already called API-0013 with nested amount `"1000"` to read `SendToName` and `SpName`.

Next calls API-0013 again with the typed amount. The button stays disabled when the amount is outside the min/max (BR-0011) or no wallet row is selected. Optional note and `inclCOFee` toggle. Success reads `responseData[0].coFee`, `totalFee`, `sendToName` and opens confirm.

The controller passes `sendToMany: true` even for one recipient. Those method arguments are not the JSON keys; the leg list is.

## SCR-0010 Confirm

**Widget:** `SendMoneyConfirmationWidget` · **Controller:** `SendMoneyConfirmationController`

Shows recipient, fee, and total. PIN length 4 copies `sourcePin` and `channelPass` onto each selected contact, then API-0014. Success opens `ReceiptScrollWidget` with `responseData[0].transId`. Overdraft uses `overDraftBrandId` and `overDraftLoanAmount`.

Dashboard local-transfer can open the schedule sheet (API-0279) instead of paying now.

Gift uses `requestSendMoneyProcessPaymentGift` (not this screen's default). Mchango uses `requestSendMoneyProcessPaymentMchango`.

## Evidence

- `lib/ui/controllers/sendmoney/send_money_enter_amount_controller.dart` @ `6328b7254`
- `lib/ui/controllers/sendmoney/send_money_confirmation_controller.dart`
- `lib/ui/widgets/sendmoney/sendmoneytransfer/send_money_enter_amount_widget.dart`
- `lib/ui/widgets/sendmoney/sendmoneytransfer/send_money_confirmation_widget.dart`
