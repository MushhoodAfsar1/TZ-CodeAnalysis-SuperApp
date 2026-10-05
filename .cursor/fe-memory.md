# FE memory

Index only. Canonical resume file for the BE-driven mobile KB. No secrets.

## Paths

| Item | Value |
|---|---|
| FE repo (read-only) | `/agent/repos/TZ-Tigo-SuperApp-Mobile` |
| FE package | `package:tigopesa` |
| Analysis repo | `/agent/repos/TZ-CodeAnalysis-SuperApp` |
| BE KB | `backend/` (read-only) |
| FE output | `mobile/` |
| Legacy `fe-mobile/` | not present on this branch |

## Pins

| Item | Value |
|---|---|
| fe_ref | `main` |
| fe_sha | `6328b7254cdae4468d124da79011cc6b30ec2087` |
| be_kb_ref | `cursor/frontend-mobile-api-analysis-ad82` |
| be_kb_sha | `2655b7a40cab39ad132db7a332cdc604cb759a77` |
| BE README repo_ref | `analysis/be/full-20261005` |

Local FE branch name may differ. Analyzed commit is `main` at this SHA. Do not checkout the FE repo.

## FE architecture (verified)

| Concern | Path |
|---|---|
| ApiManager | `lib/core/network/manager/api_ manager.dart` (space in the filename) |
| Endpoint constants | `lib/core/network/constants/network_constants.dart` › `UrlConstants` |
| NetworkManager.callDioAPI | `lib/core/network/manager/network_manager.dart` |
| Isolate HTTP status | `lib/core/network/manager/isolates_network_manager.dart` |
| Gateway token (not SESS) | `lib/core/session_networking/session_network_manager.dart` › `SessionNetworkManager.requestGenerateGateWayToken` |
| Use cases | `lib/utils/constants/app_enums.dart` › `UseCaseTypes` |
| Crypto | `lib/utils/crypto_util/crypto_util.dart` — mechanism only |
| Legacy UI | `lib/ui/controllers/` · `lib/ui/widgets/` |
| Revamp UI | `lib/ui/new_ui_revamp/` |
| Session state | `UserDataManager`, `PreferencesManager` |
| Common body | `NetworkManagerUtils.getCommonJSONRequestBody` |
| Envelope model | `lib/models/network/base_response/base_response_model.dart` › `ResponseFields` |

## Base-URL key → service

| FE prefix after `baseURL` | Service |
|---|---|
| `sessions/` | SESS |
| `accounts/` | ACCOUNT (not deeply checked) |
| `configuration/` | CONFIG |
| `sendmoney/` | SEND |
| `wallet/` | WALLET |
| `selfcare/` | SELFC |
| `loan/` | LOAN |
| gateway `oauth2/` + `token` | not in the BE KB (APIM). Do not map to SESS-001. |

Phase 1 index is not built. Add rows as services are analyzed.

## Processing order

SESS deep-analyzed. Next: `index-fe`, then ACCOUNT → WALLET → SEND → AIRTIME → EXTPAY → MERCH → LOAN → SAVING → GRPSAV → MCHANGO → INSUR → VCARD → DSTV → GSM → SELFC → REWARD → NOTIF → EXPENSE → GAMES → RESERV → STOCK → CONFIG → IDENT → AUDIT → PORTAL.

MERSET, MCHRPT, NOTSCH are `n/a` (no HTTP).

## Next free IDs

| Prefix | Next |
|---|---|
| FE-SCR | 002 |
| FE-FLW | 001 |
| FE-INT | 001 |
| FE-GAP | 006 |
| FE-API-X | 001 |
| FE-BR-SESS | 008 |
| FE-BR-APP | 001 |
| FE-BR other codes | 001 |

## Resume

SESS finished through `BE-API-SESS-004` (002 used; 001 not-in-fe; 003 and 004 n/a-helper). Do not re-analyze SESS unless `fe_sha` or `be_kb_sha` changes.

Next session: `index-fe` (ApiManager methods → endpoint, use-case, encryption). Then `analyze-service ACCOUNT`.

## Open questions

- SESS-001 `/api/Account/auth` is absent. Login stores the session JWT from ACCOUNT `LoginProfile` `accessCode`.
- Gateway client-credentials token is a separate FE call for the reverse sweep.
- Refresh `responseData` field names and HTTP 411 are not in the BE SESS contract (FE-GAP-002, FE-GAP-003).
- `accesstoken` is sent with a `Bearer ` prefix (FE-GAP-005).
- 410 retry always re-posts as POST.
- Merchant home other APIs not traced (FE-SCR-001 is partial).

## Session log

| Date | Mode | Scope | Output |
|---|---|---|---|
| 2026-10-05 | init + analyze-service | SESS | `mobile/` skeleton and SESS usage |
