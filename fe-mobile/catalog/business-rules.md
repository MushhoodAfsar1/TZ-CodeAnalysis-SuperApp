---
kb_section: fe-mobile
type: catalog
ids: [FE-CAT-BR]
feature: ALL
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---
# Business rules

Rules the app enforces on the traced flows. SESS rules BR-0001–BR-0007 are the fold of the earlier SESS slice, renumbered into this tree.

| ID | Rule | Type | Enforced in FE? | Also in BE? | Where | Screens | Conf. |
|---|---|---|---|---|---|---|---|
| BR-0001 | Refresh only in the last 35 seconds before refresh expiry, and only if the access JWT is already expired | session | yes | no | `CommonFunctions.checkAndCallRefreshLoginAuthToken` | SCR-0001, app shell | confirmed |
| BR-0002 | When refresh expiry has passed, replace the stack with login | session | yes | no | same | SCR-0003 | confirmed |
| BR-0003 | Skip refresh on logout, empty token, bad JWT, or missing expiry | session | yes | no | same | SCR-0001 | confirmed |
| BR-0004 | HTTP 410 refreshes, then retries the original call, at most twice | session | yes | BE-BR-SESS-001 / BE-ERR-SESS-002 | `NetworkManager.callDioAPI` | any | confirmed |
| BR-0005 | HTTP 411 sends a logged-in user to login | session | yes | not listed | isolate + `UserDataManager` | SCR-0003 | confirmed |
| BR-0006 | Pointer and resume checks run only while logged in | session | yes | no | `main.dart`, merchant `onResumed` | SCR-0001 | confirmed |
| BR-0007 | Session expiry does not show `sessionExpiredText` | session | yes | no | redirect to login | SCR-0003 | confirmed |
| BR-0008 | MPIN length is 4 | auth | yes | no | `AppConstants.pinCodeFieldsLength` | SCR-0003, SCR-0008, SCR-0010, SCR-0012 | confirmed |
| BR-0009 | CheckAuth `UM-Lo-04` login, `UM-Lo-01` OTP, `UM-Lo-12` self-onboard, `UM-Lo-16` device limit | auth | yes | codes not named on ACCOUNT-011 | `handleCheckAuthResponse` | SCR-0005 | confirmed |
| BR-0010 | OTP length 20 on Android and 9 on iOS; resend after `otptimeout` or 60s | auth | yes | no | `AppUtil.getOTPMaxLength` | SCR-0004 | confirmed |
| BR-0011 | Send amount between min and max; a wallet row is required | money | yes | BE amount is a decimal string, no app min | `SendMoneyEnterAmountController` | SCR-0009 | confirmed |
| BR-0012 | Cash-out consumer sends `creditParty.key` `msisdn`; merchant and Mchango use other methods | money | yes | BE-API-WALLET-001 `creditParty.value` | `cashOutLookUp` | SCR-0011 | confirmed |
| BR-0013 | ATM confirm is opened with fee string `"10.0"`. There is no fee API | money | yes | no | `AtmCashoutEnterAmountWidget.getNextButtonContainer` | SCR-0013, SCR-0014 | confirmed |
| BR-0014 | After a bank is picked, amount must sit between that row's `MinAmount` and `MaxAmount`. Tiles are min, min × 20, and max | money | yes | partner list, not a BE check | bank `onChanged` | SCR-0013 | confirmed |
| BR-0015 | Self airtime uses pre-login `airtimeMinLimit` / `airtimeMaxLimit` (fallback 100 and 10000). Other operators use the min and max passed into the screen | money | yes | no | `MobileTopupWidgetController` | SCR-0017 | confirmed |
| BR-0016 | `isOther` false posts AirTimeTopUpV1. `isOther` true posts AirTimeTopUpOthers and adds `shortCode` and `operatorName` | money | yes | two AIRTIME actions | `creditAirTimeTopUpOthers` | SCR-0018 | confirmed |
| BR-0017 | Other-bill amount must be at least 100 and not above the cached wallet `mainBalance` | money | yes | no | `EnterAmountForPayBillController` | SCR-0019 | confirmed |
| BR-0018 | Government `asseType` is `ASSESS-A`, `ASSESS-C`, or `ASSESS-E` from the flow id and the control-number chip. Next requires a reference of length at least 7 | money | yes | DTO names the field `AsseType` | `requestGovPaymentInquiry` | SCR-0021 | confirmed |
| BR-0019 | When pre-login `isvalentine` is true, category name `Valentine Day` sorts first, and a theme message `Event` supplies the gradient | gift | yes | no | `populateValentineDataAtTop`, `getThemes` | SCR-0024 | confirmed |
| BR-0020 | Gift pay posts TransferSendMoney with `userCaseName` `giftMoney` and `customData` theme keys. It is not a separate path | gift | yes | BE-BR-SEND-006 when leg type is giftMoney | `requestSendMoneyProcessPaymentGift` | SCR-0025, SCR-0010 | confirmed |

Next free rule ID: `BR-0021`.
