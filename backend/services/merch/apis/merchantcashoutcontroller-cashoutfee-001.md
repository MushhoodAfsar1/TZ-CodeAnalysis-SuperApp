---
kb_section: backend
type: api-contract
ids: [BE-API-MERCH-001]
service: MERCH
repo: TZ-Tigo-SuperApp-Merchant
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 2367767
updated: 2026-10-05
confidence: confirmed
---

# BE-API-MERCH-001 MerchantCashoutController.CashoutFee
**Service:** BE-SVC-MERCH · **Handler:** `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/MerchantCashoutController.cs › MerchantCashoutController.CashoutFee` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/MerchantCashout/CashoutFee
  internal_path: /api/MerchantCashout/CashoutFee
  dispatch_field: null
  dispatch_value: null
  controller_action: MerchantCashoutController.CashoutFee
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/MerchantCashout/CashoutFee`
- **Auth / filters:** SessionValidationFilter (X-User-Session), EncryptionProviderFilter<CashoutFeeRequest>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `CashoutFeeRequest`

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
| `MSISDN` | `string?` | N | — | shape only | MSISDN |
| `Amount` | `float` | N | — | shape only | Amount |
| `SegmentType` | `string?` | N | — | shape only | SegmentType |
| `TargetMSISDN` | `string?` | N | — | shape only | TargetMSISDN |
| `PINCode` | `int?` | N | — | shape only | PINCode |

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
  "MSISDN": "255XXXXXXXXX",
  "Amount": "<amount>",
  "SegmentType": "<string>",
  "TargetMSISDN": "255XXXXXXXXX",
  "PINCode": "<encrypted-pin>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt + session | 500 / 410 | BE-BR-MERCH-001 | `MerchantCashOutController.CashOutFee` |
| 2 | HTTP `Tanzania:CashOutFee` + header `Tanzania:CashOutAuthToken`; success needs Name+Fee | fail | — | `CashoutService.MerchantCashoutFee` |

## Internal call chain
1. Client POST `/api/MerchantCashout/CashoutFee` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `CashoutFeeRequest` on `HttpContext.Items['modeldata']`.
3. SessionValidationFilter validates `X-User-Session`.
4. `MerchantCashoutController.CashoutFee` runs (`TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/MerchantCashoutController.cs`).
5. Calls `_cashoutService.MerchantCashoutFee`.
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
  MerchantCashoutController->>_cashoutService: MerchantCashoutFee()
  MerchantCashoutController->>_apiResponseHandler: CreateResponse()
  MerchantCashoutController->>_logger: LogError()
```

## Downstream
| Order | Target | Sync/Async | Condition | Sent / used fields |
|---|---|---|---|---|
| 1 | HTTP `Tanzania:CashOutFee` | Sync | always | merchant cash-out fee fields; `Tanzania:CashOutAuthToken` |

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
| 500 | 500 | BE-ERR-MERCH-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-MERCH-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-MERCH-001` (when session filter present).

## Config keys
- `Tanzania:CashOutFee`, `Tanzania:CashOutAuthToken`

## Evidence
- `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/MerchantCashoutController.cs › MerchantCashoutController.CashoutFee` @ `2367767`
- Decrypted DTO `CashoutFeeRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
