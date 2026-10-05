---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-092]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-092 TransactionHistoryController.Create
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/TransactionHistoryController.cs › TransactionHistoryController.Create` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/TransactionHistory/create
  internal_path: /api/TransactionHistory/create
  dispatch_field: null
  dispatch_value: null
  controller_action: TransactionHistoryController.Create
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/TransactionHistory/create`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `Id` | `Int32` | N | — | shape only | Id |
| `key` | `string?` | N | — | shape only | key |
| `value` | `string?` | N | — | shape only | value |
| `entype` | `string?` | N | — | shape only | entype |
| `swtype` | `string?` | N | — | shape only | swtype |
| `enprefix` | `string?` | N | — | shape only | enprefix |
| `swprefix` | `string?` | N | — | shape only | swprefix |
| `is_title_visible` | `bool?` | N | — | shape only | is_title_visible |
| `is_receiver_name_visible` | `bool?` | N | — | shape only | is_receiver_name_visible |
| `is_receiver_msisdn_visible` | `bool?` | N | — | shape only | is_receiver_msisdn_visible |
| `image_url` | `string?` | N | — | shape only | image_url |
| `dark_image_url` | `string?` | N | — | shape only | dark_image_url |
| `image_size` | `string?` | N | — | shape only | image_size |
| `image_type` | `string?` | N | — | shape only | image_type |
| `image_name` | `string?` | N | — | shape only | image_name |
| `dark_image_size` | `string?` | N | — | shape only | dark_image_size |
| `dark_image_type` | `string?` | N | — | shape only | dark_image_type |
| `dark_image_name` | `string?` | N | — | shape only | dark_image_name |

Headers / route / query params: none parsed beyond action signature `[('request', 'TransactionHistoryDto')]`

Sample (synthetic):
```json
{
  "Id": 0,
  "key": "<string>",
  "value": "<string>",
  "entype": "<string>",
  "swtype": "<string>",
  "enprefix": "<string>",
  "swprefix": "<string>",
  "is_title_visible": false,
  "is_receiver_name_visible": false,
  "is_receiver_msisdn_visible": "255XXXXXXXXX",
  "image_url": "<string>",
  "dark_image_url": "<string>",
  "image_size": "<string>",
  "image_type": "<string>",
  "image_name": "<string>",
  "dark_image_size": "<string>",
  "dark_image_type": "<string>",
  "dark_image_name": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/TransactionHistoryController.cs › TransactionHistoryController.Create` |
| 2 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/TransactionHistoryController.cs › TransactionHistoryController.Create` |
| 3 | `String.IsNullOrEmpty(request.image_url` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/TransactionHistoryController.cs › TransactionHistoryController.Create` |
| 4 | `String.IsNullOrEmpty(request.dark_image_url` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/TransactionHistoryController.cs › TransactionHistoryController.Create` |
| 5 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/TransactionHistoryController.cs › TransactionHistoryController.Create` |

## Internal call chain
1. Client POST `/api/TransactionHistory/create`.
2. `TransactionHistoryController.Create` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/TransactionHistoryController.cs`).
3. Calls `_logger.LogDebug`.
4. Calls `MethodBase.GetCurrentMethod`.
5. Calls `MethodBase.GetCurrentMethod`.
6. Calls `Diagnostics.StackFrame`.
7. Calls `User.FindFirst`.
8. Calls `_logger.LogDebug`.
9. Calls `MethodBase.GetCurrentMethod`.
10. Calls `MethodBase.GetCurrentMethod`.
11. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>TransactionHistoryController: POST /api/TransactionHistory/create
  participant TransactionHistoryController
  TransactionHistoryController->>_logger: LogDebug()
  TransactionHistoryController->>MethodBase: GetCurrentMethod()
  TransactionHistoryController->>request: ToString()
  TransactionHistoryController->>Diagnostics: StackFrame()
  TransactionHistoryController->>User: FindFirst()
  TransactionHistoryController->>Value: ToString()
  TransactionHistoryController->>mapped: ToString()
  TransactionHistoryController->>Utilities: GetDateTime()
  TransactionHistoryController->>_transactionHistoryRepository: CreateTransactionHistoryAsync()
  TransactionHistoryController->>retdata: ToString()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/TransactionHistoryController.cs › TransactionHistoryController.Create` @ `9c00072`
- Decrypted DTO `TransactionHistoryDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
