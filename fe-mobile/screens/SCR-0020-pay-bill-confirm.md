---
kb_section: fe-mobile
type: screen
ids: [SCR-0020]
feature: billpayment
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: partial
---

# SCR-0020 Other-bill confirm (`OtherBillsPayConfirmationWidget`)

**Controller:** `OtherBillPayConfirmationController` · **Flow:** FLW-0008 · **API:** API-0037

## Entry

SCR-0019 after a successful reference inquiry. Fee and payer name come from that response.

## Actions

| Action | Validation | API | Result |
|---|---|---|---|
| PIN | Length 4 (BR-0008) | API-0037 | Receipt |

`submitBilPayment` sends `channelPass` as the PIN, `targetRefNumber` as the bill reference, `shortCode`, `amount`, `descriptionText`, `purpose`, `overdraftBrandID`, `isBankTransfer`, and `useCaseName`. `consumerID`, `referenceID`, `terminalType`, and `paymentType` come from `ExternalPaymentConstants`.

The same method is used by government confirm, bank transfer, and international remittance. Those callers are named in the API catalog. This screen file covers the other-bills confirm widget only.

## Response branches

Success opens `ReceiptScrollWidget`. An overdraft brand on the response can open an overdraft sheet before the receipt (same pattern as airtime; not re-diffed line by line). Failure shows the submit error.

A schedule button can open `ScheduleDetailsWidget`. That schedule flow is not traced.

## Evidence

- `lib/ui/controllers/billpayment/other_bill_pay_confirmation_controller.dart` @ `6328b7254`
- `lib/ui/widgets/billpayment/other_bills_pay_confirmation_widget.dart`
- `lib/core/network/manager/api_ manager.dart` › `submitBilPayment`
