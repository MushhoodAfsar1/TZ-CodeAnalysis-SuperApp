---
kb_section: fe-mobile
type: flow
ids: [FLW-0005]
feature: cash_point
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# FLW-0005 Agent cash-out

This is the cash-point flow, not ATM cash-out (`withdrawal_atm` / `getAtmCashoutGenerateOtp`, not traced).

```mermaid
flowchart LR
  recents[RecentAndFavouritesWidget cashOutAgent] --> amt[SCR-0011 amount]
  amt --> fee{account type}
  fee -->|consumer| f1[API-0039 cashOutFee]
  fee -->|merchant| f2[API-0040 merchant fee]
  fee -->|mchango| f3[cashoutFeeMchnago]
  f1 --> conf[SCR-0012 confirm and PIN]
  f2 --> conf
  f3 --> conf
  conf --> pay{account type}
  pay -->|consumer| p1[API-0041 cashOutPaymentV1]
  pay -->|merchant| p2[API-0042]
  pay -->|mchango| p3[initiateCashOutMchango]
  p1 --> receipt[OlderReceiptScrollWidget]
```

Consumer fee and payment match the deepened wallet DTOs, including `creditParty.key` = `msisdn` and `creditParty.value` = the agent id (BR-0012). Amount must sit between `cashOutMinAmount` and `cashOutMaxAmount`.

## Evidence

- `lib/ui/controllers/cash_point/cash_point_enter_amount_widget_controller.dart` › `cashOutLookUp`
- `lib/ui/controllers/cash_point/cash_point_confirmation_widget_controller.dart` › `initiateCashOut`
- `lib/core/network/manager/api_ manager.dart` › `requestCashOutfee`, `initiateCashOut`
