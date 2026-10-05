---
kb_section: fe-mobile
type: flow
ids: [FLW-0009]
feature: tanzania_gift
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: partial
---

# FLW-0009 Gift money

**APIs:** API-0096, API-0097, API-0098, API-0099 · **Screens:** SCR-0023, SCR-0024, SCR-0025, then SCR-0010 · **Rules:** BR-0008, BR-0019, BR-0020

Theme and history are gift-specific. The payment reuses send-money confirm with a gift body.

```mermaid
sequenceDiagram
  participant User
  participant Hist as SCR-0023
  participant Theme as SCR-0024
  participant Preview as SCR-0025
  participant Pay as SCR-0010
  User->>Hist: open gift
  Hist->>Hist: API-0096 top five
  User->>Theme: pick receiver
  Theme->>Theme: API-0097 categories
  Theme->>Theme: API-0098 themes
  User->>Preview: note and image
  Preview->>Pay: themeId, categoryId, message
  Pay->>Pay: API-0099 TransferSendMoney userCaseName giftMoney
```

The nested `transferMoney[].transactionType` is copied from the contact helper. The preview button does not set it to `giftMoney`.

Field diff: [../contracts/gift.md](../contracts/gift.md).

## Evidence

- `lib/ui/controllers/tanzania_gift/` @ `6328b7254`
- `lib/core/network/manager/api_ manager.dart` › `getTopFiveGiftTransaction`, `getAllThemeCatagory`, `getByIdTheme`, `requestSendMoneyProcessPaymentGift`
