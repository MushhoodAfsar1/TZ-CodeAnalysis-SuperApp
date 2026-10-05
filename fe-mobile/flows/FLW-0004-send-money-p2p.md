---
kb_section: fe-mobile
type: flow
ids: [FLW-0004]
feature: sendmoney
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: partial
---

# FLW-0004 Consumer send money (local transfer)

Primary path only. Gift, international transfer, Mchango, and the revamp confirmation widget are separate. `SendMoneyConfirmationWidgetV2` has no `Get.to` caller in `lib/`.

```mermaid
flowchart LR
  dash[Dashboard Mixx transfer] --> pick[Contact pick]
  pick --> v1[API-0013 verify amount 1000]
  v1 --> amt[SCR-0009 amount]
  amt --> v2[API-0013 verify typed amount]
  v2 --> conf[SCR-0010 confirm and PIN]
  conf --> pay[API-0014 TransferSendMoney]
  pay --> receipt[ReceiptScrollWidget]
```

Rules: amount between `sendMoneyMinAmount` and `sendMoneyMaxAmount` (operator mins for Halo, TPesa, TTCL); a wallet row must be selected; PIN length 4 (BR-0008, BR-0011). Send-to-many blocks the user's own number in the phonebook. Single-recipient P2P has no such check in `redirectToNextScreenFromContactClick`.

From the dashboard, local-transfer confirm can open `SchedulePaymentBottomSheet` instead of paying immediately (API-0279, still `path-only`).

Contract diff: [../contracts/session-auth-money.md](../contracts/session-auth-money.md).

## Evidence

- `lib/ui/controllers/contactselection/contact_selection_for_transaction_widget_controller.dart` › `requestSendMoneyGetOperatorAndNameCheckForBundles`
- `lib/ui/controllers/sendmoney/send_money_enter_amount_controller.dart` › `requestSendMoneyInitiatePayment`
- `lib/ui/controllers/sendmoney/send_money_confirmation_controller.dart` › `requestSendMoneyProcessPayment`
- `lib/core/network/manager/api_ manager.dart` › `ApiManager.requestSendMoneyInitiatePayment`, `requestSendMoneyProcessPayment`
