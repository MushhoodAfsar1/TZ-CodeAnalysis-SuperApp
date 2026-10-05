---
kb_section: fe-mobile
type: flow
ids: [FLW-0006]
feature: atm_cashout
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# FLW-0006 ATM cash-out

**APIs:** API-0158 (`BE-API-SEND-008`), API-0159 (`BE-API-SEND-009`) · **Screens:** SCR-0013, SCR-0014 · **Rules:** BR-0008, BR-0013, BR-0014

There is no fee lookup. The confirm screen is opened with a fixed fee string.

```mermaid
sequenceDiagram
  participant User
  participant Amount as SCR-0013
  participant Confirm as SCR-0014
  participant BE as SEND ATM cash-out
  User->>Amount: open ATM cash-out
  Amount->>BE: API-0158 GetATMCashoutBankList
  BE-->>Amount: responseData.ListOfATM
  User->>Amount: pick bank and amount
  Amount->>Confirm: feeAmount 10.0 and sendAmount
  User->>Confirm: PIN length 4
  Confirm->>BE: API-0159 ATMCashoutGenerateOtp
  BE-->>Confirm: envelope transactionStatus
  Confirm->>User: sheet, then consumer shell
```

Field diff: [../contracts/atm-airtime-bills.md](../contracts/atm-airtime-bills.md).

## Evidence

- `lib/ui/widgets/atm_cashout/atm_cashout_enter_amount_widget.dart` @ `6328b7254`
- `lib/core/network/manager/api_ manager.dart` › `getAtmCashoutBankList`, `getAtmCashoutGenerateOtp`
