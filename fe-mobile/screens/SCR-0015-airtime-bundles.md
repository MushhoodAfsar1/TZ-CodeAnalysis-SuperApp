---
kb_section: fe-mobile
type: screen
ids: [SCR-0015]
feature: airtimetopups
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# SCR-0015 Airtime bundles (`AirTimeTopUpsWidget`)

**Controller:** `AirTimeTopUpsWidgetController` · **Flow:** FLW-0007 · **APIs:** API-0023, API-0024

## Entry

Buy-bundle entry from the dashboard. Franchise tabs are local labels. They are not an API.

## Actions

| Action | Validation | API | Result |
|---|---|---|---|
| Load back-office bundles | Receiver MSISDN, operator type `networkBundle` | API-0023 | Stores `responseData.boBundles`. Cached under the receiver key |
| Load Saizi Yako | Same screen | API-0024 | Reads `responseData.saiziYakoBundles.recommendations.product` |
| Pick a bundle | — | — | Opens SCR-0016 |

Both calls are background unless the controller sets `onForeground`. Match stays `path-only`: the CONFIG bundle response tables were not field-diffed in this pass. The UI field names above are confirmed.

## Evidence

- `lib/ui/controllers/airtimetopups/air_time_top_ups_widget_controller.dart` › `getNetworkBoBundles`, `setNetWorkBackOfficeBundleData` @ `6328b7254`
- `lib/ui/widgets/airtimetopups/network_bundles_widget.dart` › `Get.to(AirTimeTopUpsConfirmationWidget)`
