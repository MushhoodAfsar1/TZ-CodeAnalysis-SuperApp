---
kb_section: backend
type: api-contract
ids: [BE-API-AIRTIME-005]
service: AIRTIME
repo: TZ-Tigo-SuperApp-AirTimeTopup
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 7a52359
updated: 2026-10-05
confidence: confirmed
---

# BE-API-AIRTIME-005 AirTimeController.AirTimeTopUp
**Service:** BE-SVC-AIRTIME · **Handler:** `TZ-Tigo-SuperApp-AirTimeTopup/TZTigoSuperAppAirTimeTopup/Controllers/AirTimeController.cs › AirTimeController.AirTimeTopUp` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/AirTime/AirTimeTopUp
  internal_path: /api/AirTime/AirTimeTopUp
  dispatch_field: null
  dispatch_value: null
  controller_action: AirTimeController.AirTimeTopUp
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/AirTime/AirTimeTopUp`
- **Auth / filters:** SessionValidationFilter (X-User-Session), EncryptionProviderFilter<AirTimeTopUpRequest>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `AirTimeTopUpRequest`

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
| `consumerID` | `string?` | N | — | shape only | consumerID |
| `transactionID` | `string?` | N | — | shape only | transactionID |
| `country` | `string?` | N | — | shape only | country |
| `correlationID` | `string?` | N | — | shape only | correlationID |
| `sourceMsisdn` | `string?` | N | — | shape only | sourceMsisdn |
| `targetMsisdn` | `string?` | N | — | shape only | targetMsisdn |
| `pin` | `string?` | N | — | shape only | pin |
| `providerSource` | `string?` | N | — | shape only | providerSource |
| `providerTarget` | `string?` | N | — | shape only | providerTarget |
| `walletSource` | `string?` | N | — | shape only | walletSource |
| `walletTarget` | `int` | N | — | shape only | walletTarget |
| `amount` | `int` | N | — | shape only | amount |
| `shortCode` | `string?` | N | — | shape only | shortCode |
| `operatorName` | `string?` | N | — | shape only | operatorName |
| `overDraftBrandId` | `string?` | N | — | shape only | overDraftBrandId |

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
  "consumerID": "<string>",
  "transactionID": "<string>",
  "country": "<string>",
  "correlationID": "<string>",
  "sourceMsisdn": "255XXXXXXXXX",
  "targetMsisdn": "255XXXXXXXXX",
  "pin": "<encrypted-pin>",
  "providerSource": "<string>",
  "providerTarget": "<string>",
  "walletSource": "<string>",
  "walletTarget": 0
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt + session | 500 / 410 | BE-BR-AIRTIME-001 | `AirTimeController.AirTimeTopUp` |
| 2 | Insert `airtimetopup` (AirTimeType Mixx By Yas); DB fail logged, continues | — | — | `AirTimeRepository.AirTimeTopUp` |
| 3 | SOAP TopUpRequest (`AirTimeTopUp`); V0 **ignores** overDraftBrandId | parse v3/v1 tags; update DB | — | same |
| 4 | code `topup-2002-6001-W` → remap `topup-20103-E` low-balance **fail** | fail | BE-BR-AIRTIME-002 | same |
| 5 | Else if targetMsisdn set → FCM ReceiverTopUp + success | HTTP fail → fault tags | — | same |

## Internal call chain
1. Client POST `/api/AirTime/AirTimeTopUp` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `AirTimeTopUpRequest` on `HttpContext.Items['modeldata']`.
3. SessionValidationFilter validates `X-User-Session`.
4. `AirTimeController.AirTimeTopUp` runs (`TZ-Tigo-SuperApp-AirTimeTopup/TZTigoSuperAppAirTimeTopup/Controllers/AirTimeController.cs`).
5. Calls `_airTimeRepositry.AirTimeTopUp`.
6. Calls `_responseHandler.CreateResponse`.
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
  AirTimeController->>_airTimeRepositry: AirTimeTopUp()
  AirTimeController->>_responseHandler: CreateResponse()
  AirTimeController->>_logger: LogError()
```

## Downstream
| Order | Target | Sync/Async | Condition | Sent / used fields |
|---|---|---|---|---|
| 1 | SOAP TopUp via `AirTimeTopUp` | Sync | always | source/target, pin, amount, wallets; `TanzaniaAPI:Username\|Password\|consumerId\|Debug` |
| 2 | FCM ReceiverTopUp | Sync | success + targetMsisdn | notify |
| 3 | EF `airtimetopup` | W | always | persist |

## Data touched
| Entity / table / SP | R/W | Notes |
|---|---|---|
| `airtimetopup` | W | insert + SOAP update |

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
- `AirTimeTopUp`, `TanzaniaAPI:Username`, `TanzaniaAPI:Password`, `TanzaniaAPI:consumerId`, `TanzaniaAPI:Debug`, `TokenKey`

## Evidence
- `TZ-Tigo-SuperApp-AirTimeTopup/TZTigoSuperAppAirTimeTopup/Controllers/AirTimeController.cs › AirTimeController.AirTimeTopUp` @ `7a52359`
- Decrypted DTO `AirTimeTopUpRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
