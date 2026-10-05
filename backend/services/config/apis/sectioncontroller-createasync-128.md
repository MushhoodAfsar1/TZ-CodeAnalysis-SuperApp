---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-128]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-128 SectionController.CreateAsync
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SectionController.cs › SectionController.CreateAsync` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Section/create
  internal_path: /api/Section/create
  dispatch_field: null
  dispatch_value: null
  controller_action: SectionController.CreateAsync
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Section/create`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `Id` | `Int32` | N | — | shape only | Id |
| `section_name` | `string` | N | — | shape only | section_name |
| `image_url` | `string` | N | — | shape only | image_url |
| `sort_order` | `Int32` | N | — | shape only | sort_order |
| `description` | `string` | N | — | shape only | description |
| `created_by` | `string` | N | — | shape only | created_by |
| `created_date` | `DateTime` | N | — | shape only | created_date |
| `updated_by` | `string` | N | — | shape only | updated_by |
| `updated_date` | `DateTime` | N | — | shape only | updated_date |
| `country_id` | `Int32` | N | — | shape only | country_id |
| `channel_id` | `Int32` | N | — | shape only | channel_id |
| `app_version_id` | `Int32` | N | — | shape only | app_version_id |
| `flow_id` | `string` | N | — | shape only | flow_id |
| `messages` | `List<DashboardMultilingualMessage>` | N | — | shape only | messages |
| `image_size` | `string` | N | — | shape only | image_size |
| `image_type` | `string` | N | — | shape only | image_type |
| `image_name` | `string` | N | — | shape only | image_name |
| `displayon` | `string?` | N | — | shape only | displayon |
| `is_merchant_biller` | `Boolean` | N | — | shape only | is_merchant_biller |
| `isrevamp` | `bool` | N | — | shape only | isrevamp |

Headers / route / query params: none parsed beyond action signature `[('section', 'SectionDto')]`

Sample (synthetic):
```json
{
  "Id": 0,
  "section_name": "<string>",
  "image_url": "<string>",
  "sort_order": 0,
  "description": "<string>",
  "created_by": "<string>",
  "created_date": "<iso-datetime>",
  "updated_by": "<string>",
  "updated_date": "<iso-datetime>",
  "country_id": 0,
  "channel_id": 0,
  "app_version_id": 0,
  "flow_id": "<string>",
  "messages": [],
  "image_size": "<string>",
  "image_type": "<string>",
  "image_name": "<string>",
  "displayon": "<string>",
  "is_merchant_biller": false,
  "isrevamp": false
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `string.IsNullOrEmpty(section.image_url` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SectionController.cs › SectionController.CreateAsync` |
| 2 | `!validationResult.IsValid` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SectionController.cs › SectionController.CreateAsync` |
| 3 | `validationResult.HasWarnings` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SectionController.cs › SectionController.CreateAsync` |
| 4 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SectionController.cs › SectionController.CreateAsync` |
| 5 | `_configuration.GetValue<string>("EnableLog:Warning"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SectionController.cs › SectionController.CreateAsync` |

## Internal call chain
1. Client POST `/api/Section/create`.
2. `SectionController.CreateAsync` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SectionController.cs`).
3. Calls `_logger.LogDebug`.
4. Calls `MethodBase.GetCurrentMethod`.
5. Calls `MethodBase.GetCurrentMethod`.
6. Calls `Diagnostics.StackFrame`.
7. Calls `string.IsNullOrEmpty`.
8. Calls `ImageValidationUploadHelper.ValidateAndUploadAsync`.
9. Calls `string.Join`.
10. Calls `_logger.LogWarning`.
11. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>SectionController: POST /api/Section/create
  participant SectionController
  SectionController->>_logger: LogDebug()
  SectionController->>MethodBase: GetCurrentMethod()
  SectionController->>section: ToString()
  SectionController->>Diagnostics: StackFrame()
  SectionController->>string: IsNullOrEmpty()
  SectionController->>ImageValidationUploadHelper: ValidateAndUploadAsync()
  SectionController->>string: Join()
  SectionController->>_logger: LogWarning()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SectionController.cs › SectionController.CreateAsync` @ `9c00072`
- Decrypted DTO `SectionDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
