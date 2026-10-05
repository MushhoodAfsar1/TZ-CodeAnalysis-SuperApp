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
| BR-0013 | Balance refresh control stays hidden for 30 seconds after a balance call | money | yes | no | `balanceDelayTimer` | SCR-0013 | confirmed |
| BR-0014 | A numeric savings balance of 0 clears the savings-greater-than-zero flag | money | yes | BE maps `savingPesa` | `requestGetBalanceDashboard` | SCR-0013 | confirmed |
| BR-0015 | After logout, GetBalance returns an empty completion and does not call Dio | session | yes | no | `ApiManager.requestGetBalance` | SCR-0013 | confirmed |
| BR-0016 | Top-up amount uses operator min/max when `isOther`, otherwise pre-login `airtimeMinLimit` / `airtimeMaxLimit` (fallback 100 and 10000) | money | yes | BE amount is an int | `MobileTopUPWidgetController.checkAmount` | SCR-0014 | confirmed |
| BR-0017 | Other-operator top-up does not verify when the picked number is the logged-in user | money | yes | no | contact selection `topUpOthers` | FLW-0006 | confirmed |
| BR-0018 | Pay-bill warns when the amount is above wallet `mainBalance` or below 100, and next requires a non-empty reference | money | yes | no | `EnterAmountForPayBillController` | SCR-0016 | confirmed |
| BR-0019 | Government inquiry enables when the control number length is at least 7 | money | yes | no | `EnterControlNumberWidgetController` | SCR-0018 | confirmed |

Next free rule ID: `BR-0020`.
