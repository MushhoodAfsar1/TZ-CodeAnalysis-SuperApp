---
kb_section: fe-mobile
type: flow
ids: [FLW-0006]
feature: airtimetopups
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: partial
---

# FLW-0006 Other-operator airtime top-up

Legacy contact book path for `UseCaseTypes.topUpOthers`. Self top-up (`isOther` false) uses the same confirm method and was not walked from the dashboard icon. Bundle purchase is a different widget.

```mermaid
flowchart LR
  pick[Contact pick] --> skip{Own number?}
  skip -->|yes| stop[No verify]
  skip -->|no| v[API-0257 verify amount 1000]
  v --> amt[SCR-0014 amount]
  amt --> conf[SCR-0015 PIN]
  conf --> pay[API-0258 others or API-0259 V1]
  pay --> od{overdraftbrandid?}
  od -->|yes| retry[Retry same call]
  od -->|no| receipt[ReceiptScrollWidget]
  retry --> receipt
```

Rules: do not verify the logged-in number (BR-0017). Amount must sit in the operator min/max or the pre-login airtime limits (BR-0016). PIN length 4 (BR-0008).

Contract diff: [../contracts/dashboard-airtime-bills.md](../contracts/dashboard-airtime-bills.md).

## Evidence

- `lib/ui/widgets/contactselection/contact_selection_for_transaction_widget.dart`
- `lib/ui/controllers/contactselection/contact_selection_for_transaction_widget_controller.dart` › `getOperaterTopUpOther`
- `lib/ui/controllers/airtimetopups/credit_telma/mobile_top_up_confirmation_widget_controller.dart`
