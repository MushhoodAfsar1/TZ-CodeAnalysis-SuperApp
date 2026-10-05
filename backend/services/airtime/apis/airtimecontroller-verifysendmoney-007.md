---
kb_section: backend
type: api-contract
ids: [BE-API-AIRTIME-007]
service: AIRTIME
repo: TZ-Tigo-SuperApp-AirTimeTopup
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 7a52359
updated: 2026-10-05
confidence: confirmed
---

# BE-API-AIRTIME-007 AirTimeController.VerifySendMoney
**Service:** BE-SVC-AIRTIME · **Handler:** `TZ-Tigo-SuperApp-AirTimeTopup/TZTigoSuperAppAirTimeTopup/Controllers/AirTimeController.cs › AirTimeController.VerifySendMoney` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/AirTime/VerifySendMoney
  internal_path: /api/AirTime/VerifySendMoney
  dispatch_field: null
  dispatch_value: null
  controller_action: AirTimeController.VerifySendMoney
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/AirTime/VerifySendMoney`
- **Auth / filters:** SessionValidationFilter (X-User-Session), EncryptionProviderFilter<VerifySendMoneyRequest>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `VerifySendMoneyRequest`

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `requestingOrganisationTransactionReference` | `string?` | N | — | shape only | requestingOrganisationTransactionReference |
| `requestId` | `string?` | N | — | shape only | requestId |
| `channel` | `string?` | N | — | shape only | channel |
| `ipInfo` | `string?` | N | — | shape only | ipInfo |
| `appVersion` | `string?` | N | — | shape only | appVersion |
| `languageCode` | `string?` | N | — | shape only | languageCode |
| `deviceId` | `string?` | N | — | shape only | deviceId |
| `deviceMaker` | `string?` | N | — | shape only | deviceMaker |
| `pushId` | `string?` | N | — | shape only | pushId |
| `deviceType` | `string?` | N | — | shape only | deviceType |
| `oS` | `string?` | N | — | shape only | oS |
| `geoCode` | `string?` | N | — | shape only | geoCode |
| `userCaseName` | `string?` | N | — | shape only | userCaseName |
| `accessToken` | `string?` | N | — | shape only | accessToken |
| `sendMoney` | `List<SendMoney>` | Y | one+ legs | foreach | verify legs |
| `sendMoney[].consumerID` | `string?` | overwritten | — | `VerifySendMoney:ConsumerID` | MMP consumer |
| `sendMoney[].referenceID` | `string?` | N | — | shape | MMP ref |
| `sendMoney[].sourceMSISDN` | `string?` | Y | MSISDN | MMP | payer |
| `sendMoney[].targetMSISDN` | `string?` | Y | MSISDN; TANQR prefix | MMP | payee |
| `sendMoney[].sourcePin` | `string?` | N | PIN | bill-query | PIN |
| `sendMoney[].terminalType` | `string?` | N | — | `VerifySendMoney:TerminalType` | channel |
| `sendMoney[].amount` | `string?` | Y | decimal | MMP | amount |
| `sendMoney[].shortCode` | `string?` | Y | TANQR or 50001/50024/50058 | repository | rail |
| `sendMoney[].inclCOFee` | `bool?` | N | true → ShortCode 50001 | repository | include CO fee |

Headers / route / query params: none parsed beyond action signature `[('msg', 'RequestModel')]`

Sample (synthetic):
```json
{"payload": "<ciphertext-or-json>"}
# decrypted payload:
{
  "requestingOrganisationTransactionReference": "<string>",
  "requestId": "<string>",
  "channel": "<string>",
  "ipInfo": "<encrypted-pin>",
  "appVersion": "<string>",
  "languageCode": "<string>",
  "deviceId": "<device-id>",
  "deviceMaker": "<string>",
  "pushId": "<push-token>",
  "deviceType": "<string>",
  "oS": "<string>",
  "geoCode": "<string>",
  "userCaseName": "<string>",
  "accessToken": "<jwt>",
  "sendMoney": [{ "sourceMSISDN": "255XXXXXXXXX", "targetMSISDN": "255XXXXXXXXX", "amount": "<amount>", "shortCode": "<shortcode>", "inclCOFee": false }]
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt + session | 500 / 410 | BE-BR-AIRTIME-001 | `AirTimeController.VerifySendMoney` |
| 2 | Force consumerID ← `VerifySendMoney:ConsumerID` per leg | — | — | `AirTimeRepository.VerifySendMoney` |
| 3 | shortCode == `VerifySendMoney:TANQR` → tanqrshortcode by first-3 digits | 400 Invalid Alias | — | same |
| 4 | Tigo rail if userCaseName==sendmoney OR shortCode in 50001/50024/50058 → CalculateFee (`VerifySendMoneyTigoToTigoURL`); InclCOFee → 50001 | else bill query | — | same |
| 5 | Else MTPGBillQuery (`VerifySendMoneyTigoToOtherURL`) + TerminalType | — | — | same |
| 6 | ResultCode `0` marks Status; GET `VerifySendMoney:OperatorsInformation?msisdn=` (errors swallowed) | aggregate any Status | — | same |
| 7 | Remap ResultCode via CONFIG ResponseCodeApp | mapped fail | — | controller |

## Internal call chain
1. Client POST `/api/AirTime/VerifySendMoney` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `VerifySendMoneyRequest` on `HttpContext.Items['modeldata']`.
3. SessionValidationFilter validates `X-User-Session`.
4. `AirTimeController.VerifySendMoney` runs (`TZ-Tigo-SuperApp-AirTimeTopup/TZTigoSuperAppAirTimeTopup/Controllers/AirTimeController.cs`).
5. Calls `_airTimeRepositry.VerifySendMoney`.
6. Calls `_responseHandler.ResponseObject`.
7. Calls `_responseHandler.CreateResponse`.
8. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  participant EncFilter
  App->>EncFilter: POST payload envelope
  EncFilter->>EncFilter: AES decrypt payload
  EncFilter->>AirTimeController: Items['modeldata']
  participant AirTimeController
  AirTimeController->>_airTimeRepositry: VerifySendMoney()
  AirTimeController->>_responseHandler: ResponseObject()
  AirTimeController->>_logger: LogError()
  AirTimeController->>_responseHandler: CreateResponse()
```

## Downstream
| Order | Target | Sync/Async | Condition | Sent / used fields |
|---|---|---|---|---|
| 1 | SOAP CalculateFee `VerifySendMoney:VerifySendMoneyTigoToTigoURL` | Sync | Tigo rail | ConsumerID, MSISDNs, Amount, ShortCode, InclCOFee |
| 2 | SOAP MTPGBillQuery `VerifySendMoney:VerifySendMoneyTigoToOtherURL` | Sync | other | + PIN, TerminalType |
| 3 | HTTP `VerifySendMoney:OperatorsInformation` | Sync | after MMP | msisdn |
| 4 | EF tanqrshortcode | Sync | TANQR | prefix |

## Data touched
| Entity / table / SP | R/W | Notes |
|---|---|---|
| see service `data-model.md` | mixed | not fully attributed per action |

## Response (decrypted)
| Field (JSON) | Type | Always / when | Meaning |
|---|---|---|---|
| `success` | boolean | always | handler outcome |
| `responseCode` | string | always | mapped via CONFIG when handler used |
| `transactionStatus` | string | success | mapped message |
| `errorDescription` | string | failure | mapped or static |
| `appVersionInfo` | string | often | app version hint |
| `responseData` | object | success | action-specific |

Sample (synthetic):
```json
{
  "success": true,
  "responseCode": "<code>",
  "transactionStatus": "<message>",
  "appVersionInfo": "<version>",
  "responseData": {}
}
```

## Errors
| BE code | HTTP | ID | Condition | Message key/text | Retryable |
|---|---|---|---|---|---|
| 500 | 500 | BE-ERR-AIRTIME-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-AIRTIME-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-AIRTIME-001` (when session filter present).

## Config keys
- `VerifySendMoney:ConsumerID`, `VerifySendMoney:TANQR`, `VerifySendMoney:VerifySendMoneyTigoToTigoURL`, `VerifySendMoney:VerifySendMoneyTigoToOtherURL`, `VerifySendMoney:TerminalType`, `VerifySendMoney:OperatorsInformation`, `TokenKey`

## Evidence
- `TZ-Tigo-SuperApp-AirTimeTopup/TZTigoSuperAppAirTimeTopup/Controllers/AirTimeController.cs › AirTimeController.VerifySendMoney` @ `7a52359`
- Decrypted DTO `VerifySendMoneyRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
