---
kb_section: backend
type: api-contract
ids: [BE-API-GSM-011]
service: GSM
repo: TZ-Tigo-SuperApp-GSM
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 13fe724
updated: 2026-10-05
confidence: confirmed
---

# BE-API-GSM-011 GSMBundlesController.CheckBalanceAirtimeSmsAndCallV2
**Service:** BE-SVC-GSM · **Handler:** `TZ-Tigo-SuperApp-GSM/TZTigoSuperAppGSM/Controllers/GSMBundlesController.cs › GSMBundlesController.CheckBalanceAirtimeSmsAndCallV2` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/GSMBundles/CheckBalanceAirtimeSmsAndCallV2
  internal_path: /api/GSMBundles/CheckBalanceAirtimeSmsAndCallV2
  dispatch_field: null
  dispatch_value: null
  controller_action: GSMBundlesController.CheckBalanceAirtimeSmsAndCallV2
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/GSMBundles/CheckBalanceAirtimeSmsAndCallV2`
- **Auth / filters:** EncryptionProviderFilter<CheckBalanceAirtimeSmsAndCallRequest>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `CheckBalanceAirtimeSmsAndCallRequest`

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `requestingOrganisationTransactionReference` | `string` | N | — | shape only | requestingOrganisationTransactionReference |
| `requestId` | `string?` | N | — | shape only | requestId |
| `iPInfo` | `string` | N | — | shape only | iPInfo |
| `geoCode` | `string` | N | — | shape only | geoCode |
| `useCaseName` | `string` | N | — | shape only | useCaseName |
| `channel` | `string` | N | — | shape only | channel |
| `appVersion` | `string` | N | — | shape only | appVersion |
| `languageCode` | `string` | N | — | shape only | languageCode |
| `deviceId` | `string` | N | — | shape only | deviceId |
| `deviceMaker` | `string` | N | — | shape only | deviceMaker |
| `oS` | `string` | N | — | shape only | oS |
| `accessToken` | `string` | N | — | shape only | accessToken |
| `featureId` | `string` | N | — | shape only | featureId |
| `sourceNode` | `string` | N | — | shape only | sourceNode |
| `sessionId` | `string` | N | — | shape only | sessionId |
| `country` | `string` | N | — | shape only | country |
| `timeStamp` | `string` | N | — | shape only | timeStamp |
| `dataset` | `List<param>` | N | — | shape only | dataset |

Headers / route / query params: none parsed beyond action signature `[('msg', 'RequestModel')]`

Sample (synthetic):
```json
{"payload": "<ciphertext-or-json>"}
# decrypted payload:
{
  "requestingOrganisationTransactionReference": "<string>",
  "requestId": "<string>",
  "iPInfo": "<encrypted-pin>",
  "geoCode": "<string>",
  "useCaseName": "<string>",
  "channel": "<string>",
  "appVersion": "<string>",
  "languageCode": "<string>",
  "deviceId": "<device-id>",
  "deviceMaker": "<string>",
  "oS": "<string>",
  "accessToken": "<jwt>",
  "featureId": "<string>",
  "sourceNode": "<string>",
  "sessionId": "<string>",
  "country": "<string>",
  "timeStamp": "<string>",
  "dataset": []
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt `payload` with AES when config `is_encrypted`/`isEncrypted` is true; else JSON-deserialize | Filter stores raw string; later cast may fail → 500 | — | `TZ-Tigo-SuperApp-GSM/TZTigoSuperAppGSM/Controllers/GSMBundlesController.cs › GSMBundlesController.CheckBalanceAirtimeSmsAndCallV2` |
| 2 | `cacheData != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-GSM/TZTigoSuperAppGSM/Controllers/GSMBundlesController.cs › GSMBundlesController.CheckBalanceAirtimeSmsAndCallV2` |
| 3 | `!string.IsNullOrWhiteSpace(resultAccountType` | branch / error envelope | — | `TZ-Tigo-SuperApp-GSM/TZTigoSuperAppGSM/Controllers/GSMBundlesController.cs › GSMBundlesController.CheckBalanceAirtimeSmsAndCallV2` |
| 4 | `resp != "SUCCESS"` | branch / error envelope | — | `TZ-Tigo-SuperApp-GSM/TZTigoSuperAppGSM/Controllers/GSMBundlesController.cs › GSMBundlesController.CheckBalanceAirtimeSmsAndCallV2` |
| 5 | `requestDto.languageCode == "en"` | branch / error envelope | — | `TZ-Tigo-SuperApp-GSM/TZTigoSuperAppGSM/Controllers/GSMBundlesController.cs › GSMBundlesController.CheckBalanceAirtimeSmsAndCallV2` |

## Internal call chain
1. Client POST `/api/GSMBundles/CheckBalanceAirtimeSmsAndCallV2` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `CheckBalanceAirtimeSmsAndCallRequest` on `HttpContext.Items['modeldata']`.
3. `GSMBundlesController.CheckBalanceAirtimeSmsAndCallV2` runs (`TZ-Tigo-SuperApp-GSM/TZTigoSuperAppGSM/Controllers/GSMBundlesController.cs`).
4. Calls `bundleService.CheckBalanceAirtimeSmsAndCall`.
5. Calls `dataset.FirstOrDefault`.
6. Calls `id.ToLower`.
7. Calls `string.IsNullOrWhiteSpace`.
8. Calls `Utilities.CacheExpiry`.
9. Calls `_cacheService.SetData`.
10. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  participant EncFilter
  App->>EncFilter: POST payload envelope
  EncFilter->>EncFilter: AES decrypt payload
  EncFilter->>GSMBundlesController: Items['modeldata']
  participant GSMBundlesController
  GSMBundlesController->>bundleService: CheckBalanceAirtimeSmsAndCall()
  GSMBundlesController->>dataset: FirstOrDefault()
  GSMBundlesController->>id: ToLower()
  GSMBundlesController->>string: IsNullOrWhiteSpace()
  GSMBundlesController->>Utilities: CacheExpiry()
  GSMBundlesController->>_cacheService: SetData()
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
| 500 | 500 | BE-ERR-GSM-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-GSM-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-GSM-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-GSM/TZTigoSuperAppGSM/Controllers/GSMBundlesController.cs › GSMBundlesController.CheckBalanceAirtimeSmsAndCallV2` @ `13fe724`
- Decrypted DTO `CheckBalanceAirtimeSmsAndCallRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
