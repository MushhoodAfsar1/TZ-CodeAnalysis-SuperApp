---
kb_section: fe-mobile
type: contract-diff
ids: [API-0018, API-0034, API-0035, API-0037, API-0049, API-0257, API-0258, API-0259]
feature: dashboard-airtime-bills
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: partial
---

# Contract diff — dashboard balance, airtime top-up, bill pay

Diff of live FE calls against backend contracts on `main` @ `0c13cc4`. FE `main` @ `6328b7254`. Field names only. Hosts are omitted.

Wire shape is `{ "payload": "<ciphertext>" }` via `CryptoUtil.encrypt`. `NetworkResponseKeysConstants.isEncryptionDone` is true.

Common body from `NetworkManagerUtils.getCommonJSONRequestBody`: `iPInfo`, `channel`, `appVersion`, `languageCode`, `deviceId`, `deviceMaker`, `deviceType`, `oS`, `pushId`, and either `geoCode` or `latitude`/`longitude`, plus `msisdn` when the caller passes one. The `isPushIdRequired` argument does not change the map; `pushId` is always included. When `isGeoCodeRequired` is true and device coordinates are empty, `geoCode` is a fixed fallback pair (the pair is not copied here).

`iPInfo` versus DTO `ipInfo` on AIRTIME and EXTPAY is the same casing conflict as GAP-0109.

## API-0018 · BE-API-WALLET-006 GetBalance · contract-mismatch

| FE key | Sent | BE `GetBalanceRequest` | Note |
|---|---|---|---|
| `requestingOrganisationTransactionReference` | Y | Y optional | |
| `userCaseName` | Y (`registration`) | DTO lists `useCaseName` | GAP-0110 extended |
| `mpin` | Y (stored consumer or merchant PIN) | not on the DTO | GAP-0120 |
| `accountMSISDN` | Y | Y | Merchant path sends the merchant number as passed. Consumer path adds the country code. |
| `iPInfo` | Y | Y `iPInfo` | Casing matches this DTO. |
| `latitude`, `longitude` | Y (`isGeoCodeRequired: false`) | DTO has `geoCode`, not these keys | GAP-0120 |
| `requestID`, `accesstoken` | N | optional | Session rides the `X-User-Session` header. |

A logout flag returns the completion with an empty body and does not call Dio (BR-0015).

Success stores `GetBalanceResponseModel` when `responseData` is present. The parser reads `responseData.tigoPesa`, `savingPesa`, `wallet3`, `wallet4`. BE-BR-WALLET-005 maps those names when MMP `resultCode` is `0`. The published response sample leaves `responseData` empty (GAP-0121). The model's `toJson` writes `wallet3` and `wallet4` from the savings field; the UI uses `fromJson`, so the screen still shows the four balances it parsed.

## API-0257 · BE-API-AIRTIME-007 VerifySendMoney · contract-mismatch

Top-level JSON is `userCaseName` (`sendMoney`), `requestingOrganisationTransactionReference`, and `sendMoney`. The airtime DTO property is `userCaseName`, so this key matches (unlike ACCOUNT login). Method arguments `amount`, `senderMsisdn`, `receiverMsisdn`, and `sendToMany` are not copied into the map.

The other-operator contact step builds one `sendMoney` leg with amount `"1000"`, `inclCOFee` false, a Tigo Pesa short code, `terminalType` `USD`, and the stored PIN on `sourcePin` / `channelPass`, then opens the amount screen. The same placeholder-amount pattern as GAP-0113, on the airtime verify path (GAP-0123).

The amount screen reads `responseData[0].sendToName`, `sendToNum`, `operatorName`, `min`, `max`, `shortcode`, and the theme icon URL. The airtime verify response table is still the generic envelope.

Own-number selection does not call verify (BR-0017).

## API-0049 / API-0258 / API-0259 · BE-API-AIRTIME-006 and BE-API-AIRTIME-008 · contract-mismatch

`creditAirTimeTopUp` (API-0049) has no file-level caller. It posts the same V1 path as API-0259 without `overDraftBrandId`.

`creditAirTimeTopUpOthers` posts `AirTimeTopUpOthers` when `isOther` is true (API-0258, BE-API-AIRTIME-008) and `AirTimeTopUpV1` otherwise (API-0259, BE-API-AIRTIME-006). `shortCode` and `operatorName` are added only on the others branch.

| FE key | Sent | BE `AirTimeTopUpRequest` | Note |
|---|---|---|---|
| `userCaseName` | Y (`creditAirTimeTopUp`) | Y | |
| `country` | Y | Y | |
| `sourceMsisdn` | Y, country code | Y | |
| `targetMsisdn` | Y, country code | Y | |
| `pin` | Y, 4-digit field or stored PIN on overdraft retry | Y | |
| `amount` | Y, JSON string | `int` | GAP-0122 |
| `overDraftBrandId` | Y on 0258/0259 | Y | Empty until the overdraft sheet retries. |
| `shortCode`, `operatorName` | Y only when `isOther` | Y optional | |
| `msisdn` | Y via common body, without country code | not on the DTO | Extra key. |
| `iPInfo` | Y | DTO lists `ipInfo` | GAP-0109 |

The receipt reads `responseData.body.topUpResponse.responseBody.transactionId`. An `additionalResults.parameterType[0].parameterName` of `overdraftbrandid` opens the overdraft sheet and retries the same call. The published response sample does not list that path.

## API-0034 · BE-API-EXTPAY-001 ValidateBillerDetails · contract-mismatch

Pay-bill amount inquiry. `sourcePIN` is the method `pin` argument (the amount controller passes it empty). `amount` is stripped of spaces, currency text, and commas. `isBankTransfer` is the FE key; the DTO publishes `IsBankTransfer` (GAP-0124). `descriptionText` is not on the DTO. `consumerID`, `referenceID`, and `terminalType` come from `ExternalPaymentConstants`.

The amount screen parses `responseData.fee`, `billDueAmount`, `totalAmount`, `totalCharge`, `serviceCharge`, `controlNumber`, `brandID`, `billPayer`, `billPayee`. Bank transfer uses the same method from another controller and was not re-walked.

## API-0037 · BE-API-EXTPAY-002 SubmitBillPayment · contract-mismatch

Confirm sends `channelPass` as the 4-digit PIN, `sourceMSISDN` with country code (merchant entity number when the merchant flag is set), `amount`, `shortCode`, `targetRefNumber`, `purpose`, `paymentType`, `useCaseName`, and `isBankTransfer`. The overdraft key on the wire is `overdraftBrandID`. The DTO lists `overDraftBrandId` (GAP-0125). `descriptionText` is not on the DTO. `overDraftLoanAmount`, `productUserKey`, and `invoicePeriod` are not set by this method.

The detail controller reads `SubmitBillPaymentResponse`, including `responseData.transID`, `serviceCharge`, `totalDebit`, `newBalance`, `overDraftBrandId`, and `overDraftLoanAmount`. Bank, registration, international-remittance, and Mchango callers of the same or sibling methods were not re-diffed.

## API-0035 · BE-API-EXTPAY-003 GovernmentPaymentInquiry · contract-mismatch

`sourceMSISDN` is sent and is not on `GovernmentPaymentInquiryRequest`. Case differs on the assessment fields (GAP-0126):

| FE key | BE DTO |
|---|---|
| `asseTypeValue` | `AsseTypeValue` |
| `asseType` | `AsseType` |
| `spCode` | `SpCode` |
| `resultUrl` | `ResultUrl` |

`asseType` is `ASSESS-A` for a control number. Dawasa non-control uses `ASSESS-C`. Tarura and traffic-police non-control use `ASSESS-E`. The `isPolice` argument is not written into the JSON; `flowId` selects the branch. `spCode` is the police constant for police, the literal `SP99860` for Tarura when the entry is not a control number, and empty otherwise. Traffic police on pre-prod and prod also sets `resultUrl` to a callback string that contains a random number and a literal `</ResultUrl` fragment. The host is not recorded. Commented PSP and system-id keys are not sent.

The control-number screen parses `responseData.resp.GepgBillChkResp`, including `BillHdr.SpName` and `BillDtl[].BillAmt`, `MinPayAmt`, `PyrName`.
