---
kb_section: backend
type: api-contract
ids: [BE-API-MERCH-014]
service: MERCH
repo: TZ-Tigo-SuperApp-Merchant
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 2367767
updated: 2026-10-05
confidence: confirmed
---

# BE-API-MERCH-014 RequestToPayController.BillerCallback
**Service:** BE-SVC-MERCH · **Handler:** `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs › RequestToPayController.BillerCallback` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/RequestToPay/BillerCallback
  internal_path: /api/RequestToPay/BillerCallback
  dispatch_field: null
  dispatch_value: null
  controller_action: RequestToPayController.BillerCallback
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/RequestToPay/BillerCallback`
- **Auth / filters:** none on action (pipeline may still authorize)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
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
| `referenceID` | `string` | N | — | shape only | referenceID |
| `amount` | `string` | N | — | shape only | amount |
| `mfsTransactionID` | `string` | N | — | shape only | mfsTransactionID |
| `description` | `string` | N | — | shape only | description |
| `status` | `string` | N | — | shape only | status |

Headers / route / query params: none parsed beyond action signature `[('request', 'BillerCallbackRequest')]`

Sample (synthetic):
```json
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
  "referenceID": "<string>",
  "amount": "<amount>",
  "mfsTransactionID": "<string>",
  "description": "<string>",
  "status": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `string.IsNullOrEmpty(request.mfsTransactionID` | branch / error envelope | — | `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs › RequestToPayController.BillerCallback` |
| 2 | `requestToPay == null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs › RequestToPayController.BillerCallback` |
| 3 | `!isUpdated` | branch / error envelope | — | `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs › RequestToPayController.BillerCallback` |
| 4 | `_configuration.GetValue<string>("EnableLog:Error"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs › RequestToPayController.BillerCallback` |
| 5 | `param is string` | branch / error envelope | — | `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs › RequestToPayController.BillerCallback` |

## Internal call chain
1. Client POST `/api/RequestToPay/BillerCallback`.
2. `RequestToPayController.BillerCallback` runs (`TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs`).
3. Calls `_requestToPayService.BillerCallback`.
4. Calls `_apiResponseHandler.CreateResponse`.
5. Calls `_apiResponseHandler.CreateResponse`.
6. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>RequestToPayController: POST /api/RequestToPay/BillerCallback
  participant RequestToPayController
  RequestToPayController->>_requestToPayService: BillerCallback()
  RequestToPayController->>_apiResponseHandler: CreateResponse()
  RequestToPayController->>_logger: LogError()
```

## Downstream
| Order | Target (BE-API / BE-INT / BE-EVT) | Sync/Async | Condition | Sent / used fields |
|---|---|---|---|---|
| 1 | BE-API-CONFIG (ResponseCodeApp get-response-code-details) | Sync | after handler | responseCode, language, channel, optional service/method |

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
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs › RequestToPayController.BillerCallback` @ `2367767`
- Decrypted DTO `BillerCallbackRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
