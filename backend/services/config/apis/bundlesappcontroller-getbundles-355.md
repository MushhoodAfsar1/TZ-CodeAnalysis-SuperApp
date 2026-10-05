---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-355]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-355 BundlesAppController.GetBundles
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/BundlesAppController.cs › BundlesAppController.GetBundles` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/BundlesApp/GetBundles
  internal_path: /api/BundlesApp/GetBundles
  dispatch_field: null
  dispatch_value: null
  controller_action: BundlesAppController.GetBundles
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/BundlesApp/GetBundles`
- **Auth / filters:** SessionValidationFilter (X-User-Session), EncryptionProviderFilter<BundlesRequest>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `BundlesRequest`

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `requestingOrganisationTransactionReference` | `string` | N | — | shape only | requestingOrganisationTransactionReference |
| `iPInfo` | `string` | N | — | shape only | iPInfo |
| `geoCode` | `string` | N | — | shape only | geoCode |
| `useCaseName` | `string` | N | — | shape only | useCaseName |
| `channel` | `string` | N | — | shape only | channel |
| `appVersion` | `string` | N | — | shape only | appVersion |
| `languageCode` | `string` | N | — | shape only | languageCode |
| `deviceId` | `string` | N | — | shape only | deviceId |
| `deviceMaker` | `string` | N | — | shape only | deviceMaker |
| `oS` | `string` | N | — | shape only | oS |
| `accesstoken` | `string` | N | — | shape only | accesstoken |
| `deviceType` | `string` | N | — | shape only | deviceType |
| `requestId` | `string` | N | — | shape only | requestId |
| `msisdn` | `string` | N | — | shape only | msisdn |
| `targetmsisdn` | `string` | N | — | shape only | targetmsisdn |
| `languageId` | `string` | N | — | shape only | languageId |
| `transactionId` | `string` | N | — | shape only | transactionId |
| `operatorType` | `string` | N | — | shape only | operatorType |

Headers / route / query params: none parsed beyond action signature `[('msg', 'RequestModel')]`

Sample (synthetic):
```json
{"payload": "<ciphertext-or-json>"}
# decrypted payload:
{
  "requestingOrganisationTransactionReference": "<string>",
  "iPInfo": "<encrypted-pin>",
  "geoCode": "<string>",
  "useCaseName": "<string>",
  "channel": "<string>",
  "appVersion": "<string>",
  "languageCode": "<string>",
  "deviceId": "<device-id>",
  "deviceMaker": "<string>",
  "oS": "<string>",
  "accesstoken": "<jwt>",
  "deviceType": "<string>",
  "requestId": "<string>",
  "msisdn": "255XXXXXXXXX",
  "targetmsisdn": "255XXXXXXXXX",
  "languageId": "<string>",
  "transactionId": "<string>",
  "operatorType": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt `payload` with AES when config `is_encrypted`/`isEncrypted` is true; else JSON-deserialize | Filter stores raw string; later cast may fail → 500 | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/BundlesAppController.cs › BundlesAppController.GetBundles` |
| 2 | Validate `X-User-Session` JWT (`TokenKey`) then Redis/DB token | HTTP 410 envelope | BE-BR-CONFIG-001 | `TZ-Tigo-SuperApp-Configuration › SessionValidationFilter` |
| 3 | `response.success == false` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/BundlesAppController.cs › BundlesAppController.GetBundles` |
| 4 | `cacheData != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/BundlesAppController.cs › BundlesAppController.GetBundles` |
| 5 | `customerTypeNode.Count > 0` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/BundlesAppController.cs › BundlesAppController.GetBundles` |
| 6 | `!string.IsNullOrWhiteSpace(subscriberType` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/BundlesAppController.cs › BundlesAppController.GetBundles` |
| 7 | `bundlesRequest.targetmsisdn == bundlesRequest.msisdn` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/BundlesAppController.cs › BundlesAppController.GetBundles` |
| 8 | `saiziYakoResponse != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/BundlesAppController.cs › BundlesAppController.GetBundles` |
| 9 | `saiziYakoResponse.recommendations.product.Count > 0` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/BundlesAppController.cs › BundlesAppController.GetBundles` |
| 10 | `cacheDBData != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/BundlesAppController.cs › BundlesAppController.GetBundles` |
| 11 | `list != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/BundlesAppController.cs › BundlesAppController.GetBundles` |
| 12 | `_configuration.GetValue<string>("EnableLog:Error"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/BundlesAppController.cs › BundlesAppController.GetBundles` |

## Internal call chain
1. Client POST `/api/BundlesApp/GetBundles` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `BundlesRequest` on `HttpContext.Items['modeldata']`.
3. SessionValidationFilter validates `X-User-Session`.
4. `BundlesAppController.GetBundles` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/BundlesAppController.cs`).
5. Calls `_bundlesService.GetBundles`.
6. Calls `this.StatusCode`.
7. Calls `this.StatusCode`.
8. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  participant EncFilter
  App->>EncFilter: POST payload envelope
  EncFilter->>EncFilter: AES decrypt payload
  EncFilter->>BundlesAppController: Items['modeldata']
  participant BundlesAppController
  BundlesAppController->>_bundlesService: GetBundles()
  BundlesAppController->>_logger: LogError()
  BundlesAppController->>Message: ToString()
```

## Downstream
| Order | Target (BE-API / BE-INT / BE-EVT) | Sync/Async | Condition | Sent / used fields |
|---|---|---|---|---|
| — | none parsed beyond in-process services | — | — | — |

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
| 500 | 500 | BE-ERR-CONFIG-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-CONFIG-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-CONFIG-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/BundlesAppController.cs › BundlesAppController.GetBundles` @ `9c00072`
- Decrypted DTO `BundlesRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
