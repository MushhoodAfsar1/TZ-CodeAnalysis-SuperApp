---
kb_section: fe-mobile
type: screen
ids: [SCR-0016]
feature: airtimetopups
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# SCR-0016 Bundle confirm (`AirTimeTopUpsConfirmationWidget`)

**Controller:** `AirTimeTopUpsPackageConfirmationWidgetController` · **Flow:** FLW-0007 · **API:** API-0044

## Entry

SCR-0015 after a bundle is selected. The widget also has its own receipt navigation on some branches.

## Actions

| Action | Validation | API | Result |
|---|---|---|---|
| Confirm | PIN collected by the confirm widget | API-0044 | Receipt uses `responseData.transactionId` |

`subscribeAirTimeBundle` defaults `desiredPaymentMethod` to `"2"`. The method receives `amount` and does not put that string in the JSON. `additionalParameters` sends `PIN` (the typed PIN), `Price` (`MFS_PRICE` when the method is not `"1"`, otherwise `OCS_PRICE`), and `Language` (selected locale, upper case). `channelId` is `"21"`. `comment` is `Fulfillment`.

`payingCustomerID` is the logged-in MSISDN with country code. `fulfillmentCustomerID` is the receiver MSISDN with country code.

## Response branches

Success tracks a bundle purchase and opens `ReceiptScrollWidget` with `transactionId`. Failure stays on the confirm screen via the shared error dialog.

## Evidence

- `lib/ui/controllers/airtimetopups/air_time_top_ups_package_confirmation_widget_controller.dart` › `subscribeAirTimeBundle` @ `6328b7254`
- `lib/core/network/manager/api_ manager.dart` › `requestProductProvision`
