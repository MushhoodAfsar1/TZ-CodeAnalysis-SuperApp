# FE Analysis Agent — Memory

> Read first, update last. Index only. No secrets.

## 1. Workspace paths

| Item | Value |
|---|---|
| FE repo root (read-only) | `/agent/repos/TZ-Tigo-SuperApp-Mobile` (GitHub `AxianGroupSF/TZ-Tigo-SuperApp-Mobile`) |
| FE package root | `package:tigopesa/...` |
| FE analyzed ref | `main` |
| FE HEAD SHA at last inventory | `6328b7254cdae4468d124da79011cc6b30ec2087` |
| Analysis repo root | `/agent/repos/TZ-CodeAnalysis-SuperApp` |
| BE section path (read-only) | `backend/` |
| FE output path | `fe-mobile/` |
| Analysis repo working branch | `cursor/frontend-mobile-analysis-0ffc` |

Local FE checkout branch name may differ; the analyzed commit is `main` @ `6328b7254`. Do not checkout the FE repo.

## 2. BE knowledge layout

| Item | Value |
|---|---|
| BE index | `backend/catalog/api-catalog.md` |
| BE API ID scheme | `BE-API-<SERVICE>-###` (file `backend/services/<code>/apis/<file>.md`) |
| BE rules | `backend/catalog/business-rules.md` and `backend/services/<code>/business-rules.md` |
| BE architecture | `backend/overview/`, `backend/README.md` |
| How to match FE→BE | Lower-case `/api/...` suffix after stripping the gateway prefix (`accounts`, `sendmoney`, …) and host. HTTP method when both sides have it. Gateway prefix disambiguates only when several BE rows share the suffix. |
| Known BE quirks | GRPSAV loan paths exist twice (two controller trees, same public path): 001/057, 002/058, 003/059, 004/061, 006/060. Do not edit BE files. |

## 3. Verified FE locations

| Concern | Actual path / symbol | Verified |
|---|---|---|
| ApiManager | `lib/core/network/manager/api_ manager.dart` (space in filename) › `ApiManager` | yes |
| Endpoint constants | `lib/core/network/constants/network_constants.dart` › `UrlConstants` | yes |
| NetworkManager.callDioAPI | `lib/core/network/manager/network_manager.dart` › `NetworkManager` | yes |
| Gateway token | `lib/core/session_networking/session_network_manager.dart` › `SessionNetworkManager.requestGenerateGateWayToken` | yes |
| UseCaseTypes | `lib/utils/constants/app_enums.dart` | yes |
| UseCaseNameConstants | `lib/utils/constants/use_case_constants.dart` | yes |
| CryptoUtil | `lib/utils/crypto_util/crypto_util.dart` — mechanism only | yes |
| Legacy controllers / widgets | `lib/ui/controllers/` · `lib/ui/widgets/` | yes |
| Revamp features | `lib/ui/new_ui_revamp/` | yes |
| Response / request models | `lib/models/network/` · `lib/models/apirequests/` — not read this pass | path only |
| Session managers | `UserDataManager`, `AppDataManager`, `PreferencesManager` | yes |
| Entry | `lib/main.dart` | path only |

## 4. ID counters (next free)

| Prefix | Next |
|---|---|
| SCR | 0001 |
| FLW | 0001 |
| API | 0368 |
| BR | 0001 |
| INT | 0022 |
| GAP | 0105 |

## 5. Coverage

API inventory done (367 live calls). Every feature folder is `not-started` for screens. See `fe-mobile/_meta/coverage.md`.

Totals: screens 0 · APIs 367 (path-only 284 / fe-only 83 / be-only grouped, not individually IDed) · rules 0 · gaps 104 · integrations 21

Zero file-level callers: 38 APIs (possible dead code).

## 6. Resume point

- 2026-10-05 — API inventory complete through `API-0367`. Next session: screen inventory and deep pass for session/auth. Start at `lib/ui/controllers/splash/splash_controller.dart`, then `login`, `otp`, `onboarding`, `registration_onboarding`, `pinchanger`, `pincode`. Do not re-parse ApiManager unless FE SHA changes.
- Ternary endpoints already split: `CreateBuyAndSellOrderStockMarket`, `GetBuyAndSellOrderStockMarket`, `creditAirTimeTopUpOthers`.
- `requestToCheckAuthV1` calls CheckAuthV2. OTP methods call GenerateOtpV2 / VerifyOtpV2 (fe-only).

## 7. Decisions

- 2026-10-05 — Analyze `main` @ `6328b7254` (local checkout is that commit).
- 2026-10-05 — Bottom sheets and dialogs get `SCR-` IDs only when a later pass shows they drive logic.
- 2026-10-05 — Commented-out ApiManager methods and unused UrlConstants get no `API-` ID.
- 2026-10-05 — `path-only` is not `matched`. Contract diff waits for the feature deep pass.
- 2026-10-05 — be-only gaps are one row per service, not one row per CONFIG admin endpoint.

## 8. Learned repo facts

- 2026-10-05 — ApiManager file name is `api_ manager.dart` (space).
- 2026-10-05 — `ApiManager.requestGenerateGateWayToken` and `callRefreshLoginAuthToken` have no return type and do not call Dio themselves.
- 2026-10-05 — `isEncryptionDone` constant is true. Gateway token sets it false.
- 2026-10-05 — `lib/utils/app_util/app_util.dart` has 2 direct Dio hits not yet in the catalog.
- 2026-10-05 — Caller search is `ApiManager.method(` / `SessionNetworkManager.method(`. Bare internal calls are recorded as `ApiManager.<caller> (internal)`.

## 9. Open questions

| Date | Question | For | Blocks |
|---|---|---|---|
| 2026-10-05 | Is OTP V2 (`GenerateOtpV2` / `VerifyOtpV2`) a backend route missing from the catalog, or a stale FE path? | BE | GAP rows for those APIs |
| 2026-10-05 | Two Group Saving trees publish the same loan paths. Which tree is production? | BE | GRPSAV loan contract pick |
| 2026-10-05 | 38 live methods have no `ApiManager.method(` caller. Dead, or invoked by tear-off / reflection? | FE | Do not delete from catalog; confirm before calling them unused in a deep pass |

## 10. Session log (newest first)

| Date | Mode | Scope | Output | FE SHA |
|---|---|---|---|---|
| 2026-10-05 | init + API inventory | all live callDioAPI | `fe-mobile/` skeleton, api catalog, gaps, unmapped | 6328b7254 |
