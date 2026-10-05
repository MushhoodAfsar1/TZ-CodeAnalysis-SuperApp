---
kb_section: fe-mobile
type: screen
ids: [SCR-0018]
feature: airtimetopups
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# SCR-0018 Credit top-up confirm (`MobileTopUPConfirmationWidget`)

**Controller:** `MobileTopupConfirmationWidgetController` · **Flow:** FLW-0007 · **APIs:** API-0259 (self), API-0258 (other operator)

## Entry

SCR-0017. The same method is also called from the revamp top-up confirm controller. That revamp screen is not given an ID here.

## Actions

| Action | Validation | API | Result |
|---|---|---|---|
| PIN or biometrics | Length 4, or stored biometric secret | API-0259 when `isOther` is false. API-0258 when true | Receipt or overdraft sheet |

Self omits `shortCode` and `operatorName`. Other sends `networkShortCode` and `operator`. Both send `sourceMsisdn`, `targetMsisdn`, `pin`, `amount` (string, currency stripped), `country`, `userCaseName` `creditAirTimeTopUp`, and `overDraftBrandId` (empty unless the overdraft sheet retries).

## Response branches

The controller walks `responseData.body.topUpResponse.responseBody.additionalResults.parameterType`. When the first item's name is `overdraftbrandid` and its value is non-empty, an overdraft sheet retries the same call with `overDraftBrandId` set. Otherwise `ReceiptScrollWidget` uses `responseData` transaction id and envelope `transactionStatus`.

Failure clears the PIN.

`API-0049` `creditAirTimeTopUp` still has no caller. The live self path is API-0259.

## Evidence

- `lib/ui/controllers/airtimetopups/credit_telma/mobile_top_up_confirmation_widget_controller.dart` › `creditAirTimeTop`, `apiCallingResponse` @ `6328b7254`
- `lib/models/network/airtimetopups/tanzania_credit_air_time_top_up_response_model.dart`
