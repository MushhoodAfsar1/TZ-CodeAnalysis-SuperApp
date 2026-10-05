---
kb_section: fe-mobile
type: contract-diff
ids: [API-0096, API-0097, API-0098, API-0099]
feature: tanzania_gift
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# Contract diff — gift

FE `main` @ `6328b7254`. Backend `main` @ `0c13cc4`. These four methods build the JSON in the method. They do not call `getCommonJSONRequestBody` except API-0099.

## API-0096 · BE-API-SEND-012 GetTopFiveGiftTransaction · contract-mismatch

FE sends `msisdn`, `iPInfo`, `geoCode`, `channel`, `appVersion`, `languageCode`, `deviceId`, `deviceMaker`, `oS`, `accesstoken`, `deviceType`.

| FE | BE `GetTopFiveGiftTransactionRequest` | Note |
|---|---|---|
| `iPInfo` | `ipInfo` | GAP-0128 |
| `accesstoken` | `accessToken` | GAP-0128 |
| `msisdn` | `msisdn` | Logged-in number with country code |

The list reads `responseData.receiverResult` and `senderResult`. The published response sample does not list them (GAP-0128).

## API-0097 · BE-API-CONFIG-377 ThemesApp GetAll · contract-mismatch

`BaseModelRequest` already uses `iPInfo` and `accesstoken`, which matches this call. FE also sends `msisdn`. That key is not on `BaseModelRequest` (GAP-0129). `useCaseName` is not sent.

The UI reads `responseData[].id`, `name`, `iconUrl`.

## API-0098 · BE-API-CONFIG-378 ThemesApp GetById · contract-mismatch

FE sends `id` and `categoryId` as the same integer, plus the same device block and `msisdn`. `GiftThemesAppDto` lists `id` and `categoryId` as `int` and does not list `msisdn` (GAP-0129).

The UI reads `responseData[].id`, `imageUrl`, `message`, `bgColor`, `foreground`.

## API-0099 · BE-API-SEND-011 TransferSendMoney · contract-mismatch

Same path as API-0014. `userCaseName` is `giftMoney`. A code comment says the backend still wants a change.

`customData` items, key then value:

| key | value source |
|---|---|
| `themeid` | selected theme id |
| `categoryid` | selected category id |
| `categoryURL` | category image |
| `themeURL` | theme image |
| `message` | note |
| `receiverName` | agent or receiver name |
| `transTime` | current gift timestamp |
| `senderImage` | profile image field |
| `senderName` | login `username` |

BE-API-SEND-011 writes `giftmoneyrecord` when the leg `transactionType` is `giftMoney` and `customData` is present (BE-BR-SEND-006). The nested `transactionType` is whatever the contact helper already held. SCR-0025 does not assign `giftMoney` (GAP-0130).

`amount`, `mpin`, and `noteText` are method arguments. The JSON shown above does not copy `mpin` or `noteText` as top-level keys. The PIN still has to be on each `transferMoney` leg before this method runs; that copy was traced for API-0014 and not re-opened here.
