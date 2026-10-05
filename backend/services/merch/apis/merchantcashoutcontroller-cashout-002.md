---
kb_section: backend
type: api-contract
ids: [BE-API-MERCH-002]
service: MERCH
repo: TZ-Tigo-SuperApp-Merchant
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 2367767
updated: 2026-10-05
confidence: confirmed
---

# BE-API-MERCH-002 MerchantCashoutController.CashOut
**Service:** BE-SVC-MERCH · **Handler:** `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/MerchantCashoutController.cs › MerchantCashoutController.CashOut` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/MerchantCashout/CashoutPayment
  internal_path: /api/MerchantCashout/CashoutPayment
  dispatch_field: null
  dispatch_value: null
  controller_action: MerchantCashoutController.CashOut
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/MerchantCashout/CashoutPayment`
- **Auth / filters:** SessionValidationFilter (X-User-Session), EncryptionProviderFilter<CashOutRequest>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `CashOutRequest`

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
| `oS` | `string?` | N | — | shape only | oS |
| `geoCode` | `string?` | N | — | shape only | geoCode |
| `userCaseName` | `string?` | N | — | shape only | userCaseName |
| `accessToken` | `string?` | N | — | shape only | accessToken |
| `pushId` | `string?` | N | — | shape only | pushId |
| `deviceType` | `string?` | N | — | shape only | deviceType |
| `EntityUsername` | `string?` | N | — | shape only | EntityUsername |
| `MSISDN` | `string?` | N | — | shape only | MSISDN |
| `EAN` | `string?` | N | — | shape only | EAN |
| `SegmentType` | `string?` | N | — | shape only | SegmentType |
| `Amount` | `float` | N | — | shape only | Amount |
| `AgentID` | `string?` | N | — | shape only | AgentID |
| `PINCode` | `string?` | N | — | shape only | PINCode |
| `LanguageCode` | `string?` | N | — | shape only | LanguageCode |
| `EntityContactDetails` | `List<EntityContactDetailCashout>?` | N | — | shape only | EntityContactDetails |

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
  "oS": "<string>",
  "geoCode": "<string>",
  "userCaseName": "<string>",
  "accessToken": "<jwt>",
  "pushId": "<push-token>",
  "deviceType": "<string>",
  "EntityUsername": "<string>",
  "MSISDN": "255XXXXXXXXX",
  "EAN": "<string>",
  "SegmentType": "<string>",
  "Amount": "<amount>",
  "AgentID": "<string>",
  "PINCode": "<encrypted-pin>",
  "LanguageCode": "<string>",
  "EntityContactDetails": []
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt + session | 500 / 410 | BE-BR-MERCH-001 | `MerchantCashOutController.CashOut` |
| 2 | GetEntityDetails `Tanzania:SuperAppGetEntityDetails` ACTIVE contacts | fail | — | `CashoutService.MerchantCashOut` |
| 3 | LanguageCode en→1 else 0; Channel=`Tanzania:channel`; POST `Tanzania:CashOut` + CashOutAuthToken; persist cashout; success if TransactionID present | fail partner ErrorCode | — | same |

## Internal call chain
1. Client POST `/api/MerchantCashout/CashoutPayment` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `CashOutRequest` on `HttpContext.Items['modeldata']`.
3. SessionValidationFilter validates `X-User-Session`.
4. `MerchantCashoutController.CashOut` runs (`TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/MerchantCashoutController.cs`).
5. Calls `_cashoutService.MerchantCashOut`.
6. Calls `_apiResponseHandler.CreateResponse`.
7. Calls `_apiResponseHandler.CreateResponse`.
8. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  participant EncFilter
  App->>EncFilter: POST payload envelope
  EncFilter->>EncFilter: AES decrypt payload
  EncFilter->>MerchantCashoutController: Items['modeldata']
  participant MerchantCashoutController
  MerchantCashoutController->>_cashoutService: MerchantCashOut()
  MerchantCashoutController->>_apiResponseHandler: CreateResponse()
  MerchantCashoutController->>_logger: LogError()
```

## Downstream
| Order | Target | Sync/Async | Condition | Sent / used fields |
|---|---|---|---|---|
| 1 | HTTP `Tanzania:SuperAppGetEntityDetails` | Sync | always | entity |
| 2 | HTTP `Tanzania:CashOut` | Sync | ACTIVE | EntityUsername, MSISDN, Amount, PINCode, EntityContactDetails[] |
| 3 | EF cashout | W | always | persist |

## Data touched
| Entity / table / SP | R/W | Notes |
|---|---|---|
| `cashout` | W | persist |

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
| 500 | 500 | BE-ERR-MERCH-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-MERCH-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-MERCH-001` (when session filter present).

## Config keys
- `Tanzania:SuperAppGetEntityDetails`, `Tanzania:CashOut`, `Tanzania:CashOutAuthToken`, `Tanzania:channel`

## Evidence
- `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/MerchantCashoutController.cs › MerchantCashoutController.CashOut` @ `2367767`
- Decrypted DTO `CashOutRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
