---
kb_section: fe-mobile
type: flow
ids: [FLW-0007]
feature: billpayment
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: partial
---

# FLW-0007 Pay a bill

Two entries share the submit call. Bank transfer, DStv, registration, and international remittance also call these methods and are not on this diagram.

```mermaid
flowchart LR
  other[Other bill] --> amt[SCR-0016 amount and reference]
  amt --> inq[API-0034 ValidateBillerDetails]
  inq --> pin[SCR-0017 PIN]
  gov[Government bill] --> ctl[SCR-0018 control number]
  ctl --> govinq[API-0035 GovernmentPaymentInquiry]
  govinq --> pin
  pin --> pay[API-0037 SubmitBillPayment]
```

Rules: reference non-empty; amount warnings use wallet `mainBalance` and minimum 100 (BR-0018). Control number length at least 7 (BR-0019). PIN length 4 (BR-0008).

Contract diff: [../contracts/dashboard-airtime-bills.md](../contracts/dashboard-airtime-bills.md).

## Evidence

- `lib/ui/controllers/billpayment/enter_amount_for_pay_bill_controller.dart`
- `lib/ui/controllers/billpayment/enter_control_number_widget_controller.dart`
- `lib/ui/controllers/billpayment/bill_pay_detail_controller.dart`
