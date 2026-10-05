---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-102]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-102 AirtimeOperatorController.Create
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AirtimeOperatorController.cs › AirtimeOperatorController.Create` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/AirtimeOperator/Create
  internal_path: /api/AirtimeOperator/Create
  dispatch_field: null
  dispatch_value: null
  controller_action: AirtimeOperatorController.Create
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/AirtimeOperator/Create`
- **Auth / filters:** none on action (pipeline may still authorize)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `id` | `int?` | N | — | shape only | id |
| `operatorName` | `string?` | N | — | shape only | operatorName |
| `businessNumber` | `string?` | N | — | shape only | businessNumber |
| `brand` | `string?` | N | — | shape only | brand |
| `shortcode` | `string?` | N | — | shape only | shortcode |
| `prefixes` | `string?` | N | — | shape only | prefixes |
| `darkiconUrl` | `string?` | N | — | shape only | darkiconUrl |
| `lighticonUrl` | `string?` | N | — | shape only | lighticonUrl |
| `minimumAmount` | `decimal` | N | — | shape only | minimumAmount |
| `maximumAmount` | `decimal` | N | — | shape only | maximumAmount |
| `disabledMessage` | `string?` | N | — | shape only | disabledMessage |
| `isdisabled` | `bool` | N | — | shape only | isdisabled |
| `image_url` | `string?` | N | — | shape only | image_url |
| `lightimage_url` | `string?` | N | — | shape only | lightimage_url |

Headers / route / query params: none parsed beyond action signature `[('request', 'AirtimeOperatorDto')]`

Sample (synthetic):
```json
{
  "id": 0,
  "operatorName": "<string>",
  "businessNumber": "<string>",
  "brand": "<string>",
  "shortcode": "<string>",
  "prefixes": "<string>",
  "darkiconUrl": "<string>",
  "lighticonUrl": "<string>",
  "minimumAmount": "<amount>",
  "maximumAmount": "<amount>",
  "disabledMessage": "<string>",
  "isdisabled": false,
  "image_url": "<string>",
  "lightimage_url": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `!string.IsNullOrEmpty(request.darkiconUrl` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AirtimeOperatorController.cs › AirtimeOperatorController.Create` |
| 2 | `!string.IsNullOrEmpty(request.lighticonUrl` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AirtimeOperatorController.cs › AirtimeOperatorController.Create` |
| 3 | `format == "svg+xml"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AirtimeOperatorController.cs › AirtimeOperatorController.Create` |
| 4 | `_configuration.GetValue<string>("UploadOnAzureStorage"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AirtimeOperatorController.cs › AirtimeOperatorController.Create` |
| 5 | `format == "svg+xml"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AirtimeOperatorController.cs › AirtimeOperatorController.Create` |
| 6 | `_configuration.GetValue<string>("UploadOnAzureStorage"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AirtimeOperatorController.cs › AirtimeOperatorController.Create` |
| 7 | `imageSubCategoriesList != null && imageSubCategoriesList.Data != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AirtimeOperatorController.cs › AirtimeOperatorController.Create` |
| 8 | `subCategoryId != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AirtimeOperatorController.cs › AirtimeOperatorController.Create` |

## Internal call chain
1. Client POST `/api/AirtimeOperator/Create`.
2. `AirtimeOperatorController.Create` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AirtimeOperatorController.cs`).
3. Calls `User.FindFirst`.
4. Calls `string.IsNullOrEmpty`.
5. Calls `rg.Match`.
6. Calls `FileHelper.Base64ToImage`.
7. Calls `_cloudStorage.UploadWithTypeAsync`.
8. Calls `string.IsNullOrEmpty`.
9. Calls `rg.Match`.
10. Calls `FileHelper.Base64ToImage`.
11. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>AirtimeOperatorController: POST /api/AirtimeOperator/Create
  participant AirtimeOperatorController
  AirtimeOperatorController->>User: FindFirst()
  AirtimeOperatorController->>Value: ToString()
  AirtimeOperatorController->>string: IsNullOrEmpty()
  AirtimeOperatorController->>rg: Match()
  AirtimeOperatorController->>FileHelper: Base64ToImage()
  AirtimeOperatorController->>_cloudStorage: UploadWithTypeAsync()
  AirtimeOperatorController->>Data: ToString()
  AirtimeOperatorController->>_airtimeOperatorRepositoryRepository: CreateAsync()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AirtimeOperatorController.cs › AirtimeOperatorController.Create` @ `9c00072`
- Decrypted DTO `AirtimeOperatorDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
