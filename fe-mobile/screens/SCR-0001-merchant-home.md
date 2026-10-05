---
kb_section: fe-mobile
type: screen
ids: [SCR-0001]
feature: homepage
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: partial
---

# SCR-0001 Merchant home (`HomePageWidget`)

**Layout:** legacy · **Controller:** `HomePageWidgetController` · **Flow:** FLW-0001

Session-refresh behaviour only. Other APIs on this shell are not traced.

## Entry

`UserDataManager.redirectToDashboardAfterTransactionComplete` builds `HomePageWidget` when `PreferenceKeys.isMerchant` is true. Consumer users go to `NewBottomNavigationBarWidget`, which does not call SESS itself. The app-shell pointer listener in `main.dart` covers that shell.

## Lifecycle

| Hook | API | Condition |
|---|---|---|
| `onResumed` | API-0003 via `CommonFunctions.checkAndCallRefreshLoginAuthToken` | `UserDataManager.isLoggedIn`, then BR-0001–BR-0003. Also calls `DashboardNewController.refreshBalanceCacheFirst` (not traced). |

`onDetached`, `onInactive`, `onPaused`, and `onHidden` do not call SESS.

## Evidence

- `lib/ui/widgets/homepage/home_page_widget.dart` › `HomePageWidget` @ `6328b7254`
- `lib/ui/controllers/homepage/home_page_widget_controller.dart` › `onResumed`
