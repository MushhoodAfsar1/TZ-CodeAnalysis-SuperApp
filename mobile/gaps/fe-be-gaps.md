---
kb_section: mobile
type: gap
ids: [FE-GAP-001, FE-GAP-002, FE-GAP-003, FE-GAP-004, FE-GAP-005]
be_ids: [BE-API-SESS-002, BE-ERR-SESS-001, BE-ERR-SESS-002]
service: SESS
repo: TZ-Tigo-SuperApp-Mobile
repo_ref: main
repo_sha: 6328b7254
be_kb_ref: cursor/frontend-mobile-api-analysis-ad82
be_kb_sha: 2655b7a
updated: 2026-10-05
confidence: confirmed
---

# FE ↔ BE gaps

| FE-GAP | Type | Description | FE evidence | BE ref | Impact | Severity | Owner | Status |
|---|---|---|---|---|---|---|---|---|
| FE-GAP-001 | request-field-missing-in-fe | Refresh sends `requestingOrganisationTransactionReference`, `accesstoken`, and `refreshtoken` only. Omitted optional `RefreshTokenDto` fields: `iPInfo`, `geoCode`, `useCaseName`, `channel`, `appVersion`, `languageCode`, `deviceId`, `deviceMaker`, `oS`, `msisdn`. | `ApiManager.requestRefreshLoginAuthToken` | BE-API-SESS-002 | Low while those fields stay optional. A later required field would fail refresh. | L | FE | open |
| FE-GAP-002 | be-doc-issue | The app reads `responseData.accesstoken`, `refreshtoken`, `refreshTokenExpiryMinutes`, `accesstokenexpirein`, and `refreshtokenexpirein`. The BE contract shows `responseData` as an empty object. The same contract lists `accesstoken` twice on the request. | `ResponseDataRefreshToken` | BE-API-SESS-002 | The join is incomplete until the session response shape is written down. The app already depends on those names. | M | BE | open |
| FE-GAP-003 | be-doc-issue | HTTP 411 is treated as an invalidated refresh token and sends a logged-in user to login. `BE-ERR-SESS` lists HTTP 500 and HTTP 410 only. | `IsolateNetworkManager` 411 branch, `RequestStatusCodesConstants.refreshTokenInvalidated` | BE-ERR-SESS-001, BE-ERR-SESS-002 | If 411 is real, the error catalogue is short. If it is not returned, this branch is dead. | M | BE | open |
| FE-GAP-004 | response-field-unused | `success`, `responseCode`, `transactionStatus`, and `errorDescription` are parsed and not used to accept or reject a refresh. `appVersionInfo` is not mapped. A non-empty `accesstoken` is enough. | `ApiManager.callRefreshLoginAuthToken`, `ResponseFields` | BE-API-SESS-002 | A failure body that still contains an access token would be stored. A mapped error description is not shown. | M | FE | open |
| FE-GAP-005 | enum/format-mismatch | `accesstoken` is stored and sent with a `Bearer ` prefix. `refreshtoken` has no prefix. The BE field is a plain string; the handler calls `Replace` and the BE file does not say what is replaced. | `CommonFunctions.handleLoginResponse`, `ApiManager.callRefreshLoginAuthToken` | BE-API-SESS-002 | Refresh can fail if the service expects a raw JWT. | M | FE | open |
