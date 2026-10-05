---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-304]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-304 BankBillersController.Create
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.Create` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/BankBillers/create
  internal_path: /api/BankBillers/create
  dispatch_field: null
  dispatch_value: null
  controller_action: BankBillersController.Create
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/BankBillers/create`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `id` | `int` | N | — | shape only | id |
| `bankId` | `int?` | N | — | shape only | bankId |
| `billerId` | `int?` | N | — | shape only | billerId |
| `name` | `string?` | N | — | shape only | name |
| `code` | `string?` | N | — | shape only | code |
| `shortCode` | `string?` | N | — | shape only | shortCode |
| `nameCheck` | `string?` | N | — | shape only | nameCheck |
| `ussdNumber` | `string?` | N | — | shape only | ussdNumber |
| `ussdCode` | `string?` | N | — | shape only | ussdCode |
| `merchantShortCode` | `string?` | N | — | shape only | merchantShortCode |
| `segment1` | `string?` | N | — | shape only | segment1 |
| `segment2` | `string?` | N | — | shape only | segment2 |
| `categoryId` | `string?` | N | — | shape only | categoryId |
| `companyOrder` | `string?` | N | — | shape only | companyOrder |
| `useViewBil` | `string?` | N | — | shape only | useViewBil |
| `status` | `string?` | N | — | shape only | status |
| `type` | `string?` | N | — | shape only | type |
| `imageUrl` | `string?` | N | — | shape only | imageUrl |
| `imageName` | `string?` | N | — | shape only | imageName |
| `imageSize` | `string?` | N | — | shape only | imageSize |
| `imageType` | `string?` | N | — | shape only | imageType |

Headers / route / query params: none parsed beyond action signature `[('banksBillersDto', 'BanksBillersDto')]`

Sample (synthetic):
```json
{
  "id": 0,
  "bankId": 0,
  "billerId": 0,
  "name": "<string>",
  "code": "<string>",
  "shortCode": "<string>",
  "nameCheck": "<string>",
  "ussdNumber": "<string>",
  "ussdCode": "<string>",
  "merchantShortCode": "<string>",
  "segment1": "<string>",
  "segment2": "<string>",
  "categoryId": "<string>",
  "companyOrder": "<string>",
  "useViewBil": "<string>",
  "status": "<string>",
  "type": "<string>",
  "imageUrl": "<string>",
  "imageName": "<string>",
  "imageSize": "<string>",
  "imageType": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `response.success == false` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.Create` |
| 2 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.Create` |
| 3 | `imageSubCategoriesList != null && imageSubCategoriesList.Data != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.Create` |
| 4 | `subCategoryId != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.Create` |
| 5 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.Create` |
| 6 | `_configuration.GetValue<string>("EnableLog:Error"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.Create` |

## Internal call chain
1. Client POST `/api/BankBillers/create`.
2. `BankBillersController.Create` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs`).
3. Calls `_logger.LogDebug`.
4. Calls `MethodBase.GetCurrentMethod`.
5. Calls `MethodBase.GetCurrentMethod`.
6. Calls `JsonConvert.SerializeObject`.
7. Calls `Diagnostics.StackFrame`.
8. Calls `_bankBillersService.CreateAsync`.
9. Calls `_logger.LogDebug`.
10. Calls `MethodBase.GetCurrentMethod`.
11. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>BankBillersController: POST /api/BankBillers/create
  participant BankBillersController
  BankBillersController->>_logger: LogDebug()
  BankBillersController->>MethodBase: GetCurrentMethod()
  BankBillersController->>Diagnostics: StackFrame()
  BankBillersController->>_bankBillersService: CreateAsync()
  BankBillersController->>_logger: LogError()
  BankBillersController->>ex: ToString()
  BankBillersController->>Message: ToString()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.Create` @ `9c00072`
- Decrypted DTO `BanksBillersDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
