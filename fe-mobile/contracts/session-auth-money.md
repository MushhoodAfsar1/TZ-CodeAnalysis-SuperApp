---
kb_section: fe-mobile
type: contract-diff
ids: [API-0001, API-0002, API-0003, API-0004, API-0013, API-0014, API-0039, API-0041, API-0202]
feature: session-auth-money
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# Contract diff — session, auth, send money, cash-out

Diff of live FE calls against backend contracts on `main` @ `0c13cc4` (refresh that deepened ACCOUNT login/OTP/CheckAuth/RegisterAccount, SEND verify/transfer, and WALLET cash-out). FE `main` @ `6328b7254`. Field names only.

Wire shape for these calls (except the gateway token) is `{ "payload": "<ciphertext>" }` via `CryptoUtil.encrypt`. `NetworkResponseKeysConstants.isEncryptionDone` is true.

Common body from `NetworkManagerUtils.getCommonJSONRequestBody`: `iPInfo`, `channel`, `appVersion`, `languageCode`, `deviceId`, `deviceMaker`, `deviceType`, `oS`, `pushId`, and either `geoCode` or `latitude`/`longitude`, plus `msisdn` when the caller passes one.

## API-0001 / API-0002 · BE-API-ACCOUNT-002 LoginProfile · contract-mismatch

| FE key | Sent | BE `LoginProfileRequest` | Note |
|---|---|---|---|
| `requestingOrganisationTransactionReference` | Y | Y optional | |
| `userCaseName` | Y (`registration`) | DTO lists `useCaseName` | GAP-0110 |
| `mpin` | Y (4-digit PIN field or stored biometric secret) | not on the published DTO | GAP-0108. Downstream text still says SOAP uses `mpin`. |
| `ismerchant` | Y (`false` on consumer; argument on merchant) | Y `bool?` | |
| `pushUpdateStatus` | Y on consumer only | Y `bool` | Merchant method omits it. |
| `msisdn` | Y via common body | not on the published DTO | GAP-0108. SOAP text says `msisdn` is sent. |
| `iPInfo` | Y | DTO lists `ipInfo` | GAP-0109 |
| `accessToken` | N | optional | |

Success path stores `responseData.accessCode` as the session JWT (`UserDataManager.authTokenForCurrentlyLoggedInUser`, with a `Bearer ` prefix) and `responseData.refreshToken` plus `refreshTokenExpiryMinutes`. The published response table only shows an empty `responseData` object (GAP-0116).

`BE-API-SESS-001` `POST /api/Account/auth` is called by the account service after SOAP login. The app does not call that path. The gateway `oauth2/token` call is API-0367, not SESS-001.

## API-0003 · BE-API-SESS-002 refreshToken · contract-mismatch

Folded from the SESS slice (PR #4) and re-checked against the same SESS contract (this refresh did not edit SESS files).

| Topic | FE | BE |
|---|---|---|
| Path | `POST sessions/api/Account/refreshToken` | `POST /api/Account/refreshToken` |
| Body | `requestingOrganisationTransactionReference`, `accesstoken`, `refreshtoken` | Those fields plus optional device/geo/channel fields the app omits (GAP-0115) |
| `accesstoken` | Includes a `Bearer ` prefix | Contract does not say the prefix is stripped (GAP-0106) |
| Success | Requires non-empty `responseData.accesstoken`. Also reads `refreshtoken`, `refreshTokenExpiryMinutes`. | Published response has no `responseData` token fields (GAP-0105) |
| HTTP 410 | Starts this refresh, then retries the original call (cap 2) | BE-ERR-SESS-002 |
| HTTP 411 | Sends a logged-in user to `LoginWidget` | Not in the SESS error list (GAP-0107) |
| Envelope `success` / `responseCode` | Parsed, not used to decide success | GAP-0117 |

## API-0004 · BE-API-ACCOUNT-011 CheckAuthV2 · contract-mismatch

The method is named `requestToCheckAuthV1`. The path is `POST accounts/api/Profile/CheckAuthV2`. `BE-API-ACCOUNT-001` (`/api/Profile/CheckAuth`) is not this call. The live `requestToCheckAuth` (non-V2) method is commented out.

| FE key | Sent | BE `CheckAuthRequest` | Note |
|---|---|---|---|
| `requestingOrganisationTransactionReference` | Y | Y | |
| `userCaseName` | Y (`registration`) | DTO lists `useCaseName` | GAP-0110 |
| `msisdn` | Y (number typed on onboarding, with country code) | not on the DTO | GAP-0111 |
| `iPInfo` | Y | `ipInfo` | GAP-0109 |

The onboarding controller branches on `responseCode` values `UM-Lo-12`, `UM-Lo-16`, `UM-Lo-01`, `UM-Lo-04`. The deepened CheckAuthV2 check list names device-limit, agent, profile, and device branches and does not name those codes.

## API-0005 / API-0006 / API-0200 / API-0201 · OTP V2 · fe-only

Paths `POST accounts/api/Otp/GenerateOtpV2` and `POST accounts/api/Otp/VerifyOtpV2` still have no catalog row (GAP-0001, GAP-0002, GAP-0027, GAP-0028).

Nearest deepened contracts, suffix not equal, so match stays `fe-only`:

| FE | Nearest BE | Extra FE keys |
|---|---|---|
| GenerateOtpV2 | BE-API-ACCOUNT-046 `/api/Otp/GenerateOtp` and BE-API-ACCOUNT-048 `/api/Otp/GenerateOtpV1` | `otpType` (`deviceRegistration` or omitted). GenerateOtp DTO has `msisdn` and no `otpType`. |
| VerifyOtpV2 | BE-API-ACCOUNT-047 `/api/Otp/VerifyOtp` and BE-API-ACCOUNT-049 `/api/Otp/VerifyOtpV1` | `otp`, optional `otpType` |

## API-0202 · BE-API-ACCOUNT-014 RegisterAccount · contract-mismatch

FE JSON uses camelCase `customerMsisdn`, `emailId`, `nidaVerificationId`, `proofNumber`. The deepened DTO publishes `CustomerMsisdn`, `EmailId`, `NidaVerificationId`, `ProofNumber` (GAP-0118). `shouldLinkAccount` and `linkmsisdn` match the published camelCase names. Shared device fields still use FE `iPInfo` vs BE `ipInfo`.

## API-0013 · BE-API-SEND-010 VerifySendMoney · contract-mismatch

| FE | BE `VerifySendMoneyRequest` | Note |
|---|---|---|
| `userCaseName` = `sendMoney` | DTO property `useCaseName`; repository reads `userCaseName` | Aligned with the repository note in the BE file |
| `receiverMsisdn` | not on the DTO | GAP-0113 |
| `sendMoney[]` | required | Nested `sourceMSISDN`, `targetMSISDN`, `amount`, `shortCode`, `sourcePin`, `inclCOFee`, `consumerID`, `referenceID` are on the FE model. BE lists those except `channelUser` / `channelPass`, which the FE model also sends. |
| Method args `amount`, `senderMsisdn` | not copied into the JSON map | Values live inside `sendMoney[]` |
| Contact step | Calls verify with nested `amount` `"1000"` before the amount screen | Placeholder, then a second verify with the typed amount |

BE response table is still the generic envelope. The amount screen reads `responseData[0].coFee`, `totalFee`, `sendToName`. The contact step reads `SendToName` and `SpName` (GAP-0119).

## API-0014 · BE-API-SEND-011 TransferSendMoney · contract-mismatch

Nested `transferMoney[]` lines up with the deepened leg list: `sourceMSISDN`, `targetMSISDN`, `amount`, `shortCode`, `inclCOFee`, `sourcePin` (BE table spells `sourcePIN`), `channelUser`, `channelPass`, `consumerID`, `referenceID`.

FE also sends top-level `shortCode`, `staffInput`, `qrType`, `isMerchant`, `userCaseName`. The DTO lists `qrType`, `isMerchant`, and `transferMoney`. It does not list top-level `shortCode` or `staffInput` (GAP-0114). `amount`, `mpin`, `noteText`, and `transId` method parameters are not written into the JSON; the PIN is copied onto each leg before the call. The receipt reads `responseData[0].transId`.

## API-0039 · BE-API-WALLET-001 cashOutFee · matched

Consumer body sends `amount`, `useCaseName` (`cashOutFee`), `country`, `correlationID`, `msisdn`, `shortCode`, and `creditParty` `{ "key": "msisdn", "value": "<agent>" }`. The deepened DTO uses `iPInfo` (same casing as the common body) and the same `creditParty` object. Optional DTO fields the consumer call does not set: `requestID`, `consumerID`, `transactionType`, `accesstoken`. The UI reads `responseData.fee` and `responseData.additionalResults[1].parameterValue`.

Merchant fee is API-0040 `BE-API-MERCH-001` (not re-diffed in this pass). Mchango uses a different method.

## API-0041 · BE-API-WALLET-002 cashOutPaymentV1 · matched

Consumer body sends `consumerID`, `country`, `useCaseName` (`cashoutpayment`), `correlationID`, `msisdn`, `mPin`, `amount`, `overDraftBrandId`, and `creditParty` `{ "key": "msisdn", "value": "<agent>" }`. Those names are on `CashOutPaymentRequestDto`. The receipt reads `responseData.transactionId` and `transactionStatus`. An overdraft sheet retries the same call with `overDraftBrandId` set, which matches BE-BR-WALLET-004.

Merchant payment is API-0042 `BE-API-MERCH-002` (not re-diffed here).
