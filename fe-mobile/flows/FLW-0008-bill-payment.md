---
kb_section: fe-mobile
type: flow
ids: [FLW-0008]
feature: billpayment
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: partial
---

# FLW-0008 Bill payment

**APIs:** API-0034, API-0035, API-0037, plus API-0012 on the other-bills list · **Screens:** SCR-0019–SCR-0022 · **Rules:** BR-0008, BR-0017, BR-0018

Other bills inquire with ValidateBillerDetails, then submit. Government bills inquire with GovernmentPaymentInquiry, then the same submit method.

```mermaid
sequenceDiagram
  participant User
  participant Other as SCR-0019
  participant OtherPay as SCR-0020
  participant Gov as SCR-0021
  participant GovPay as SCR-0022
  User->>Other: reference and amount
  Other->>Other: API-0034 ValidateBillerDetails
  Other->>OtherPay: fee, billPayer, totalAmount
  OtherPay->>OtherPay: API-0037 SubmitBillPayment
  User->>Gov: control or meter number
  Gov->>Gov: API-0035 GovernmentPaymentInquiry
  Gov->>GovPay: billDtl and shortCode
  GovPay->>GovPay: API-0037 SubmitBillPayment
```

Not traced: favorites, Zanzibar-only branches, QR from the bill widgets, and the schedule button. Bank transfer and international remittance also call API-0037. They stay on their own feature rows.

Field diff: [../contracts/atm-airtime-bills.md](../contracts/atm-airtime-bills.md).

## Evidence

- `lib/ui/controllers/billpayment/` @ `6328b7254`
- `lib/core/network/manager/api_ manager.dart` › `requestInquiryReferenceNumber`, `requestGovPaymentInquiry`, `submitBilPayment`
