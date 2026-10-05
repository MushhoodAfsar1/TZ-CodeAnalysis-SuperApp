---
kb_section: fe-mobile
type: contract-diff
ids: [API-0034, API-0035, API-0037, API-0044, API-0158, API-0159, API-0258, API-0259]
feature: atm-airtime-bills
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: confirmed
---

# Contract diff — ATM cash-out, airtime, bills

Diff against backend `main` @ `0c13cc4`. FE `main` @ `6328b7254`. Field names only. Wire shape is `{ "payload": "<ciphertext>" }` via `CryptoUtil.encrypt`.

Common body: `iPInfo`, `channel`, `appVersion`, `languageCode`, `deviceId`, `deviceMaker`, `deviceType`, `oS`, `pushId`, and either `geoCode` or `latitude`/`longitude`, plus `msisdn` when passed.

API-0023 and API-0024 stay `path-only`. SCR-0015 reads `boBundles` and `saiziYakoBundles`. The CONFIG response tables were not opened in this pass.

## API-0158 · BE-API-SEND-008 GetATMCashoutBankList · contract-mismatch

| FE key | BE `ATMCashoutBankListRequest` | Note |
|---|---|---|
| `userCaseName` | `userCaseName` | Value `atmCashoutBankList` |
| `accessToken` | `accessToken` | FE sends an empty string |
| `customerMSISDN` | `CustomerMSISDN` | GAP-0120 |
| `iPInfo` | `ipInfo` | GAP-0109 |

The list UI reads `responseData.ListOfATM[]` fields `ID`, `BankName`, `MinAmount`, `MaxAmount`, `AmountSteps`. The published response sample is an empty `responseData` object (GAP-0121).

## API-0159 · BE-API-SEND-009 ATMCashoutGenerateOtp · contract-mismatch

| FE key | BE `ATMCashoutGenerateOtpRequest` | Note |
|---|---|---|
| `customerMSISDN` | `CustomerMSISDN` | GAP-0120 |
| `atmId` | `AtmId` | GAP-0120 |
| `amount` | `Amount` | GAP-0120 |
| `pin` | `PIN` | GAP-0120 |
| `accessToken` | `accessToken` | Empty string |
| `userCaseName` | `userCaseName` | Same constant as the bank list |

The success sheet displays envelope `transactionStatus`, which the BE response table does list. Nested `ResponseStatus`, `ResponseDescription`, `ResponseCode`, and `ReferenceID` are parsed and not shown.

## API-0258 / API-0259 · BE-API-AIRTIME-008 / BE-API-AIRTIME-006 · contract-mismatch

Both calls build one JSON map. `isOther` only adds `shortCode` and `operatorName` and switches the path (BR-0016).

| FE key | `AirTimeTopUpRequest` | Note |
|---|---|---|
| `userCaseName` | `userCaseName` | `creditAirTimeTopUp` |
| `country`, `sourceMsisdn`, `targetMsisdn`, `pin`, `overDraftBrandId` | same names | |
| `amount` | `int` | FE sends a decimal string (GAP-0122) |
| `shortCode`, `operatorName` | optional | Sent only for API-0258 |
| `iPInfo` | `ipInfo` | GAP-0109 |
| `consumerID`, `transactionID`, `correlationID`, `providerSource`, `providerTarget`, `walletSource`, `walletTarget` | optional | Not sent |

Success reads `responseData.body.topUpResponse.responseBody.additionalResults.parameterType` and envelope `transactionStatus`. The AIRTIME response table does not list that SOAP body (GAP-0123). An overdraft retry sets `overDraftBrandId`, which matches the V1 check that includes OverDraftBrandID when the field is set.

## API-0044 · BE-API-GSM-013 ProductProvisionV2 · contract-mismatch

Request names that the GSM DTO lists and the app sends: `country`, `channelId`, `payingCustomerID`, `fulfillmentCustomerID`, `productId`, `desiredPaymentMethod`, `externalTransactionID`, `comment`, `additionalParameters`. GSM publishes `iPInfo`, so the common-body casing matches here.

`additionalParameters` items are `{ parameterName, parameterValue }` with names `PIN`, `Price`, and `Language`. The DTO type is `ParameterType`. Item fields are not in the BE table. `Price` is `OCS_PRICE` when `desiredPaymentMethod` is `"1"`, otherwise `MFS_PRICE`. The `amount` argument is not written into the JSON.

The receipt reads `responseData.transactionId`. The published response leaves `responseData` empty (GAP-0127). Commented-out `useCaseName`, `accessToken`, and `consumerID` are not sent.

## API-0034 · BE-API-EXTPAY-001 ValidateBillerDetails · contract-mismatch

Shared names: `consumerID`, `referenceID`, `sourceMSISDN`, `sourcePIN`, `terminalType`, `targetRefNumber`, `amount`, `shortCode`.

| FE | BE | Note |
|---|---|---|
| `isBankTransfer` | `IsBankTransfer` | GAP-0126 |
| `descriptionText` | not on the DTO | GAP-0126 |
| `iPInfo` | `ipInfo` | GAP-0109 |

The amount screen reads `responseData.fee`, `billPayer`, and `totalAmount`. The EXTPAY response sample does not list them.

## API-0035 · BE-API-EXTPAY-003 GovernmentPaymentInquiry · contract-mismatch

| FE | BE `GovernmentPaymentInquiryRequest` | Note |
|---|---|---|
| `asseType` | `AsseType` | GAP-0124 |
| `asseTypeValue` | `AsseTypeValue` | GAP-0124 |
| `spCode` | `SpCode` | GAP-0124 |
| `resultUrl` | `ResultUrl` | Sent for traffic on non-staging builds. Value not recorded. GAP-0124 |
| `sourceMSISDN` | not on the DTO | GAP-0124 |

The control-number screen reads `responseData.resp.gepgBillChkResp.billHdr.shortCode` and `billDtls.billDtl[]` (`billCtrNum`, `payOpt`). That tree is not in the published response table.

## API-0037 · BE-API-EXTPAY-002 SubmitBillPayment · contract-mismatch

Shared names: `consumerID`, `referenceID`, `channelUser`, `channelPass`, `terminalType`, `sourceMSISDN`, `targetRefNumber`, `amount`, `shortCode`, `paymentType`, `purpose`, `isBankTransfer`.

| FE | BE | Note |
|---|---|---|
| `overdraftBrandID` | `overDraftBrandId` | GAP-0125 |
| `useCaseName` | `userCaseName` | GAP-0125 |
| `descriptionText` | not on the DTO | GAP-0125 |

Government confirm reads `responseData.overDraftBrandId` before the receipt.
