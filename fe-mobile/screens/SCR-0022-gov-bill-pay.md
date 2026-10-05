---
kb_section: fe-mobile
type: screen
ids: [SCR-0022]
feature: billpayment
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: partial
---

# SCR-0022 Government bill pay (`GovBillsEnterAmountWidget` → `BillPayRegistrationConfirmationWidget`)

**Controllers:** amount widget plus `BillPayRegistrationConfirmationController` · **Flow:** FLW-0008 · **API:** API-0037

## Entry

SCR-0021 when a bill row exists. Partial payment follows `payOpt` on that row.

## Actions

| Action | Validation | API | Result |
|---|---|---|---|
| Amount | Partial vs full comes from the inquiry row | — | Opens registration confirm |
| PIN | Length 4 | API-0037 | Receipt, or an overdraft sheet when `responseData.overDraftBrandId` is set |

`BillPayDetailController` is a second submit caller (older detail widget) using the same `submitBilPayment` method. It is not a separate ID.

## Evidence

- `lib/ui/widgets/billpayment/governement_bill_enter_amount_widget.dart` @ `6328b7254`
- `lib/ui/widgets/billpayment/bill_pay_registration_confirmation_widget.dart`
- `lib/ui/controllers/billpayment/bill_pay_registration_confirmation_controller.dart`
