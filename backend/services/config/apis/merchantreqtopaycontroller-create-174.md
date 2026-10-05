---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-174]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-174 MerchantReqToPayController.Create
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MerchantReqToPayController.cs › MerchantReqToPayController.Create` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/MerchantReqToPay/Create
  internal_path: /api/MerchantReqToPay/Create
  dispatch_field: null
  dispatch_value: null
  controller_action: MerchantReqToPayController.Create
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/MerchantReqToPay/Create`
- **Auth / filters:** none on action (pipeline may still authorize)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `id` | `int` | N | — | shape only | id |
| `maxAmount` | `decimal` | N | — | shape only | maxAmount |
| `maxDescriptionLength` | `int` | N | — | shape only | maxDescriptionLength |
| `requestExpiryTimeInMinutes` | `int` | N | — | shape only | requestExpiryTimeInMinutes |
| `dailyRequestLimit` | `int` | N | — | shape only | dailyRequestLimit |
| `hourlyRequestLimit` | `int` | N | — | shape only | hourlyRequestLimit |
| `maxDailyTransactionValue` | `decimal` | N | — | shape only | maxDailyTransactionValue |
| `maxHourlyTransactionValue` | `decimal` | N | — | shape only | maxHourlyTransactionValue |

Headers / route / query params: none parsed beyond action signature `[('request', 'MerchantReqToPayDTO')]`

Sample (synthetic):
```json
{
  "id": 0,
  "maxAmount": "<amount>",
  "maxDescriptionLength": 0,
  "requestExpiryTimeInMinutes": "<imei>",
  "dailyRequestLimit": 0,
  "hourlyRequestLimit": 0,
  "maxDailyTransactionValue": 0,
  "maxHourlyTransactionValue": 0
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `imageSubCategoriesList != null && imageSubCategoriesList.Data != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MerchantReqToPayController.cs › MerchantReqToPayController.Create` |
| 2 | `subCategoryId != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MerchantReqToPayController.cs › MerchantReqToPayController.Create` |
| 3 | `_configuration.GetValue<string>("EnableLog:Error"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MerchantReqToPayController.cs › MerchantReqToPayController.Create` |

## Internal call chain
1. Client POST `/api/MerchantReqToPay/Create`.
2. `MerchantReqToPayController.Create` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MerchantReqToPayController.cs`).
3. Calls `User.FindFirst`.
4. Calls `_merchantReqToPayRepository.CreateAsync`.
5. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>MerchantReqToPayController: POST /api/MerchantReqToPay/Create
  participant MerchantReqToPayController
  MerchantReqToPayController->>User: FindFirst()
  MerchantReqToPayController->>Value: ToString()
  MerchantReqToPayController->>_merchantReqToPayRepository: CreateAsync()
  MerchantReqToPayController->>_logger: LogError()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MerchantReqToPayController.cs › MerchantReqToPayController.Create` @ `9c00072`
- Decrypted DTO `MerchantReqToPayDTO` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
