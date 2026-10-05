---
kb_section: mobile
type: screen
ids: [FE-SCR-001]
be_ids: [BE-API-SESS-002]
service: SESS
repo: TZ-Tigo-SuperApp-Mobile
repo_ref: main
repo_sha: 6328b7254
be_kb_ref: cursor/frontend-mobile-api-analysis-ad82
be_kb_sha: 2655b7a
updated: 2026-10-05
confidence: partial
---

# FE-SCR-001 Merchant home (`HomePageWidget`)
**Layout:** legacy · **Controller:** `HomePageWidgetController` (`lib/ui/controllers/homepage/home_page_widget_controller.dart`) · **Services:** SESS
**Purpose:** Merchant shell after login. On resume it checks whether the session access token should be refreshed.

This file covers the session-refresh behaviour only. Other APIs on this screen are not traced yet.

## Entry points

| From | Action | Args | Guard |
|---|---|---|---|
| Post-transaction redirect | `UserDataManager.redirectToDashboardAfterTransactionComplete` builds `HomePageWidget` when `PreferenceKeys.isMerchant` is true | none | Merchant preference. Consumer users are sent to `NewBottomNavigationBarWidget` instead, which does not call SESS itself. |

## Lifecycle-triggered calls

| Hook | BE-API / local source | Condition |
|---|---|---|
| `onResumed` | BE-API-SESS-002 via `CommonFunctions.checkAndCallRefreshLoginAuthToken` | `UserDataManager.isLoggedIn`. The window, logout, and token checks are in the API file. Also calls `DashboardNewController.refreshBalanceCacheFirst` (local / other service, not traced here). |

`onDetached`, `onInactive`, `onPaused`, and `onHidden` do not call SESS.

## User actions

| Action | Validations (FE-BR) | BE-API(s) in order | Navigation result |
|---|---|---|---|
| Return to the app | FE-BR-SESS-001, FE-BR-SESS-002, FE-BR-SESS-003, FE-BR-SESS-006 | BE-API-SESS-002 when the window matches | Success stays here. Refresh expiry or a bad access token replaces the stack with `LoginWidget` (FE-BR-SESS-007). |

Request and response detail: [../services/sess/apis/accountcontroller-refresh-002.md](../services/sess/apis/accountcontroller-refresh-002.md).

## UI logic not tied to an API

Bottom-nav labels are loaded in `getHomeBottomNavigationItems` from localization keys (home, service client, scan QR, self care, profile). That list is not part of the refresh call.

## Side effects

The refresh call's token writes are in the API file. This screen does not show a loader for it.

## Evidence

- `lib/ui/widgets/homepage/home_page_widget.dart › HomePageWidget` @ `6328b7254`
- `lib/ui/controllers/homepage/home_page_widget_controller.dart › HomePageWidgetController.onResumed`
- `lib/core/app_manager/user_data_manager.dart › UserDataManager.redirectToDashboardAfterTransactionComplete`

## Open questions

- Which other backend APIs this merchant shell calls (balance, menus, banners) — later services.
- Whether every merchant build still mounts `HomePageWidget`, or some merchants now use the revamp shell. The resume hook exists only on this controller.
