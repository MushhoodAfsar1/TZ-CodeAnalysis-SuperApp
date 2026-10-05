---
kb_section: fe-mobile
type: screen
ids: [SCR-0016, SCR-0017, SCR-0018]
feature: billpayment
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: partial
---

# SCR-0016–0018 Bill pay

**Flow:** FLW-0007 · **APIs:** API-0034, API-0035, API-0037

## SCR-0016 Pay-bill amount

**Widget:** `EnterAmountForPayBillWidget` · **Controller:** `EnterAmountForPayBillController`

Reference (meter) must be non-empty. The typed amount is compared with wallet `mainBalance` and with `billPaymentMinAmount` (100) for the warning flags (BR-0018). Next calls API-0034. The controller treats a successful envelope as enough to continue; fee fields live on `responseData` (`fee`, `billDueAmount`, `totalAmount`, `brandID`, `billPayer`).

## SCR-0017 Pay-bill confirm

**Widget:** `BillPayDetailWidget` · **Controller:** `BillPayDetailController`

PIN length 4 enables confirm and calls API-0037 with the reference as `targetRefNumber`. Success parses `SubmitBillPaymentResponse` (`transID`, charges, `newBalance`, overdraft fields). Registration and other-bills confirmation controllers call the same method and were not given separate IDs.

## SCR-0018 Control number

**Widget:** `EnterControlNumberWidget` · **Controller:** `EnterControlNumberWidgetController`

The button enables when the control number length is at least 7 (BR-0019). Inquiry is API-0035. `flowId` selects Dawasa, Tarura, or traffic police. The screen reads `GovPaymentInquiryResponse` (`BillAmt`, `MinPayAmt`, `PyrName`, `SpName`). Zanzibar and the older bill-payment controller call the same method.

## Evidence

- `lib/ui/controllers/billpayment/enter_amount_for_pay_bill_controller.dart`
- `lib/ui/controllers/billpayment/bill_pay_detail_controller.dart`
- `lib/ui/controllers/billpayment/enter_control_number_widget_controller.dart`
- `lib/ui/widgets/billpayment/enter_amount_for_pay_bill_widget.dart`
- `lib/ui/widgets/billpayment/bill_pay_detail_widget.dart`
- `lib/ui/widgets/billpayment/enter_control_number_widget.dart`
- `lib/core/network/manager/api_ manager.dart` › `requestInquiryReferenceNumber`, `requestGovPaymentInquiry`, `submitBilPayment`
