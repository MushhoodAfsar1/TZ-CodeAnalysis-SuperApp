---
kb_section: backend
type: api-contract
ids: [BE-API-ACCOUNT-027]
service: ACCOUNT
repo: TZ-Tigo-SuperApp-Account
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 5c549d6
updated: 2026-10-05
confidence: confirmed
---

# BE-API-ACCOUNT-027 FavouritesController.AddFavourite
**Service:** BE-SVC-ACCOUNT · **Handler:** `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.AddFavourite` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Favourites/AddFavourite
  internal_path: /api/Favourites/AddFavourite
  dispatch_field: null
  dispatch_value: null
  controller_action: FavouritesController.AddFavourite
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Favourites/AddFavourite`
- **Auth / filters:** SessionValidationFilter (X-User-Session), EncryptionProviderFilter<FavouritesAddRequest>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `FavouritesAddRequest`

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `requestingOrganisationTransactionReference` | `string?` | N | — | shape only | requestingOrganisationTransactionReference |
| `requestID` | `string?` | N | — | shape only | requestID |
| `channel` | `string?` | N | — | shape only | channel |
| `ipInfo` | `string?` | N | — | shape only | ipInfo |
| `appVersion` | `string?` | N | — | shape only | appVersion |
| `languageCode` | `string?` | N | — | shape only | languageCode |
| `deviceId` | `string?` | N | — | shape only | deviceId |
| `deviceMaker` | `string?` | N | — | shape only | deviceMaker |
| `deviceType` | `string?` | N | — | shape only | deviceType |
| `oS` | `string?` | N | — | shape only | oS |
| `pushId` | `string?` | N | — | shape only | pushId |
| `geoCode` | `string?` | N | — | shape only | geoCode |
| `latitude` | `string?` | N | — | shape only | latitude |
| `longitude` | `string?` | N | — | shape only | longitude |
| `useCaseName` | `string?` | N | — | shape only | useCaseName |
| `accessToken` | `string?` | N | — | shape only | accessToken |
| `id` | `int` | N | — | shape only | id |
| `msisdn` | `string` | N | — | shape only | msisdn |
| `flowId` | `string` | N | — | shape only | flowId |
| `jsonRequest` | `dynamic` | N | — | shape only | jsonRequest |
| `uniqueId` | `string` | N | — | shape only | uniqueId |
| `operationType` | `string` | N | — | shape only | operationType |
| `sectionItemId` | `int?` | N | — | shape only | sectionItemId |
| `subsectionItemId` | `int?` | N | — | shape only | subsectionItemId |
| `lightImageUrl` | `string?` | N | — | shape only | lightImageUrl |
| `darkImageUrl` | `string?` | N | — | shape only | darkImageUrl |

Headers / route / query params: none parsed beyond action signature `[('msg', 'RequestModel')]`

Sample (synthetic):
```json
{"payload": "<ciphertext-or-json>"}
# decrypted payload:
{
  "requestingOrganisationTransactionReference": "<string>",
  "requestID": "<string>",
  "channel": "<string>",
  "ipInfo": "<encrypted-pin>",
  "appVersion": "<string>",
  "languageCode": "<string>",
  "deviceId": "<device-id>",
  "deviceMaker": "<string>",
  "deviceType": "<string>",
  "oS": "<string>",
  "pushId": "<push-token>",
  "geoCode": "<string>",
  "latitude": "<lat>",
  "longitude": "<lng>",
  "useCaseName": "<string>",
  "accessToken": "<jwt>",
  "id": 0,
  "msisdn": "255XXXXXXXXX",
  "flowId": "<string>",
  "jsonRequest": "<string>",
  "uniqueId": "<string>",
  "operationType": "<string>",
  "sectionItemId": 0,
  "subsectionItemId": 0,
  "lightImageUrl": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt `payload` with AES when config `is_encrypted`/`isEncrypted` is true; else JSON-deserialize | Filter stores raw string; later cast may fail → 500 | — | `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.AddFavourite` |
| 2 | Validate `X-User-Session` JWT (`TokenKey`) then Redis/DB token | HTTP 410 envelope | BE-BR-ACCOUNT-001 | `TZ-Tigo-SuperApp-Account › SessionValidationFilter` |
| 3 | `HasStoreLabel(request` | branch / error envelope | — | `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.AddFavourite` |
| 4 | `cacheData != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.AddFavourite` |
| 5 | `Convert.ToInt64(request.jsonRequest.shortCode` | branch / error envelope | — | `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.AddFavourite` |
| 6 | `Convert.ToInt64(request.jsonRequest.shortCode` | branch / error envelope | — | `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.AddFavourite` |
| 7 | `result != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.AddFavourite` |
| 8 | `request.operationType == "Add"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.AddFavourite` |
| 9 | `result.isdeleted == true` | branch / error envelope | — | `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.AddFavourite` |
| 10 | `request.subsectionItemId > 0` | branch / error envelope | — | `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.AddFavourite` |
| 11 | `_configuration.GetValue<string>("EnableLog:Error"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.AddFavourite` |

## Internal call chain
1. Client POST `/api/Favourites/AddFavourite` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `FavouritesAddRequest` on `HttpContext.Items['modeldata']`.
3. SessionValidationFilter validates `X-User-Session`.
4. `FavouritesController.AddFavourite` runs (`TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs`).
5. Calls `_favouritesService.AddFavourite`.
6. Calls `_responseHandler.CreateResponse`.
7. Calls `this.StatusCode`.
8. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  participant EncFilter
  App->>EncFilter: POST payload envelope
  EncFilter->>EncFilter: AES decrypt payload
  EncFilter->>FavouritesController: Items['modeldata']
  participant FavouritesController
  FavouritesController->>_favouritesService: AddFavourite()
  FavouritesController->>_responseHandler: CreateResponse()
  FavouritesController->>_logger: LogError()
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
| 500 | 500 | BE-ERR-ACCOUNT-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-ACCOUNT-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-ACCOUNT-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.AddFavourite` @ `5c549d6`
- Decrypted DTO `FavouritesAddRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
