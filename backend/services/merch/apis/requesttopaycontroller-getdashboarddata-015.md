---
kb_section: backend
type: api-contract
ids: [BE-API-MERCH-015]
service: MERCH
repo: TZ-Tigo-SuperApp-Merchant
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 2367767
updated: 2026-10-05
confidence: confirmed
---

# BE-API-MERCH-015 RequestToPayController.GetDashboardData
**Service:** BE-SVC-MERCH · **Handler:** `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs › RequestToPayController.GetDashboardData` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/RequestToPay/GetDashboardData
  internal_path: /api/RequestToPay/GetDashboardData
  dispatch_field: null
  dispatch_value: null
  controller_action: RequestToPayController.GetDashboardData
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/RequestToPay/GetDashboardData`
- **Auth / filters:** SessionValidationFilter (X-User-Session), EncryptionProviderFilter<GetDashboardDataDTO>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `GetDashboardDataDTO`

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
| `msisdn` | `string` | N | — | shape only | msisdn |
| `statusType` | `string` | N | — | shape only | statusType |
| `startDate` | `string?` | N | — | shape only | startDate |
| `endDate` | `string?` | N | — | shape only | endDate |

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
  "msisdn": "255XXXXXXXXX",
  "statusType": "<string>",
  "startDate": "<string>",
  "endDate": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt `payload` with AES when config `is_encrypted`/`isEncrypted` is true; else JSON-deserialize | Filter stores raw string; later cast may fail → 500 | — | `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs › RequestToPayController.GetDashboardData` |
| 2 | Validate `X-User-Session` JWT (`TokenKey`) then Redis/DB token | HTTP 410 envelope | BE-BR-MERCH-001 | `TZ-Tigo-SuperApp-Merchant › SessionValidationFilter` |
| 3 | `string.IsNullOrEmpty(request.msisdn` | branch / error envelope | — | `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs › RequestToPayController.GetDashboardData` |
| 4 | `requests == null \|\| !requests.Any(` | branch / error envelope | — | `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs › RequestToPayController.GetDashboardData` |
| 5 | `_configuration.GetValue<string>("EnableLog:Error"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs › RequestToPayController.GetDashboardData` |
| 6 | `param is string` | branch / error envelope | — | `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs › RequestToPayController.GetDashboardData` |

## Internal call chain
1. Client POST `/api/RequestToPay/GetDashboardData` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `GetDashboardDataDTO` on `HttpContext.Items['modeldata']`.
3. SessionValidationFilter validates `X-User-Session`.
4. `RequestToPayController.GetDashboardData` runs (`TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs`).
5. Calls `_requestToPayService.GetDashboardData`.
6. Calls `_apiResponseHandler.CreateResponse`.
7. Calls `_apiResponseHandler.CreateResponse`.
8. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  participant EncFilter
  App->>EncFilter: POST payload envelope
  EncFilter->>EncFilter: AES decrypt payload
  EncFilter->>RequestToPayController: Items['modeldata']
  participant RequestToPayController
  RequestToPayController->>_requestToPayService: GetDashboardData()
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
- `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs › RequestToPayController.GetDashboardData` @ `2367767`
- Decrypted DTO `GetDashboardDataDTO` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
