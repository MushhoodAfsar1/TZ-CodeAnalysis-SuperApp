---
kb_section: fe-mobile
type: screen
ids: [SCR-0014, SCR-0015]
feature: airtimetopups
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: partial
---

# SCR-0014–0015 Mobile airtime top-up

**Flow:** FLW-0006 · **APIs:** API-0257, API-0258, API-0259

## SCR-0014 Amount

**Widget:** `MobileTopUPWidget` · **Controller:** `MobileTopUPWidgetController`

Opened after other-operator contact pick (API-0257). The verify response supplies operator name, icon, short code, and min/max. The next button uses `checkAmount`: other operators must fall between those min/max values; Tigo top-up uses `airtimeMinLimit` / `airtimeMaxLimit` from pre-login, falling back to 100 and 10000 (BR-0016). Description is collected and is not a field on the credit call.

## SCR-0015 Confirm

**Widget:** `MobileTopUPConfirmationWidget` · **Controller:** `MobileTopupConfirmationWidgetController`

PIN length 4 (BR-0008) calls `creditAirTimeTopUpOthers`. `isOther` chooses API-0258 or API-0259. Target is the receiver with country code. Amount is the numeric string without currency. Success opens `ReceiptScrollWidget` with `responseData.body.topUpResponse.responseBody.transactionId` and writes a recent contact. A response parameter named `overdraftbrandid` opens `OverDraftSendMoneyBottomSheet` and retries the same call with that brand id and the PIN still in the field.

Bundle purchase (`requestProductProvision`, API-0044) and the bundle list (API-0023, API-0024) stay on this feature and are not diffed here. Revamp top-up calls the same three ApiManager methods.

## Evidence

- `lib/ui/widgets/contactselection/contact_selection_for_transaction_widget.dart` › `UseCaseTypes.topUpOthers`
- `lib/ui/controllers/airtimetopups/credit_telma/mobile_top_up_widget_controller.dart`
- `lib/ui/controllers/airtimetopups/credit_telma/mobile_top_up_confirmation_widget_controller.dart` › `creditAirTimeTop`
- `lib/ui/widgets/airtimetopups/credit_telma/mobile_topup_widget.dart`
- `lib/ui/widgets/airtimetopups/credit_telma/mobile_topup_confirmation_widget.dart`
