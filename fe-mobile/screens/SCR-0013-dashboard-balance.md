---
kb_section: fe-mobile
type: screen
ids: [SCR-0013]
feature: dashboard
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: partial
---

# SCR-0013 Dashboard wallet balance

**Flow:** home shell · **API:** API-0018

**Widget:** `DashboardScrollWidget` · **Controller:** `DashBoardWidgetController`

`callInitialAPIs` loads the balance in the background about 600ms after landing, unless a language change refreshes menus instead. `requestGetBalanceDashboard` hides the refresh control for 30 seconds (BR-0013), then calls API-0018 with the logged-in number and `onForeground: false`. Failures set `isBalanceApiFailed` and do not show the error dialog (`showErrorOnFailureResponse: false`).

Success copies `GetBalanceResponseModel` into `UserDataManager`. A numeric savings balance of `0` clears `isSavingsAccountBalanceGreaterThanZero` (BR-0014). The four displayed keys are `tigoPesa`, `savingPesa`, `wallet3`, and `wallet4`.

Merchant home uses `DashboardBaseController.requestGetBalance` with `isMerchant: true` and the merchant entity number, and only applies the result when the caller is the merchant or Mchango selection path. Revamp `DashboardNewController` and `YasDashboardController` call the same ApiManager method and are not separate screen IDs here.

Menus, banners, and GSM airtime/SMS/data (API-0043) on this widget are not traced in this pass.

## Evidence

- `lib/ui/widgets/dashboard/dashboard_scroll_widget.dart` @ `6328b7254`
- `lib/ui/controllers/dashboard/dashboard_widget_controller.dart` › `requestGetBalanceDashboard`, `callInitialAPIs`
- `lib/ui/controllers/dashboard/dashboard_base_controller.dart` › `requestGetBalance`
- `lib/core/network/manager/api_ manager.dart` › `ApiManager.requestGetBalance`
- `lib/models/network/getbalance/get_balance_response_model.dart`
