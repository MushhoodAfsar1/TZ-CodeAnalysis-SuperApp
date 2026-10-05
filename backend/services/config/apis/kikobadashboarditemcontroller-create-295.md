---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-295]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-295 KikobaDashboardItemController.Create
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/KikobaDashboardItemController.cs › KikobaDashboardItemController.Create` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/KikobaDashboardItem/create
  internal_path: /api/KikobaDashboardItem/create
  dispatch_field: null
  dispatch_value: null
  controller_action: KikobaDashboardItemController.Create
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/KikobaDashboardItem/create`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `Id` | `int` | N | — | shape only | Id |
| `flow_id` | `string` | N | — | shape only | flow_id |
| `title` | `string` | N | — | shape only | title |
| `icon_light` | `string?` | N | — | shape only | icon_light |
| `icon_dark` | `string?` | N | — | shape only | icon_dark |
| `is_enabled` | `bool` | N | — | shape only | is_enabled |
| `roles` | `List<string>` | N | — | shape only | roles |
| `item_order` | `int` | N | — | shape only | item_order |
| `parent_id` | `int?` | N | — | shape only | parent_id |
| `description` | `string?` | N | — | shape only | description |
| `group_type` | `int?` | N | — | shape only | group_type |
| `created_by` | `string?` | N | — | shape only | created_by |
| `created_date` | `DateTime` | N | — | shape only | created_date |
| `updated_by` | `string?` | N | — | shape only | updated_by |
| `updated_date` | `DateTime?` | N | — | shape only | updated_date |

Headers / route / query params: none parsed beyond action signature `[('dto', 'KikobaDashboardItemDto')]`

Sample (synthetic):
```json
{
  "Id": 0,
  "flow_id": "<string>",
  "title": "<string>",
  "icon_light": "<string>",
  "icon_dark": "<string>",
  "is_enabled": false,
  "roles": [],
  "item_order": 0,
  "parent_id": 0,
  "description": "<string>",
  "group_type": 0,
  "created_by": "<string>",
  "created_date": "<iso-datetime>",
  "updated_by": "<string>",
  "updated_date": "<iso-datetime>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `string.IsNullOrEmpty(dto.flow_id` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/KikobaDashboardItemController.cs › KikobaDashboardItemController.Create` |
| 2 | `await _repository.FlowIdExistsAsync(dto.flow_id` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/KikobaDashboardItemController.cs › KikobaDashboardItemController.Create` |
| 3 | `dto.parent_id.HasValue` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/KikobaDashboardItemController.cs › KikobaDashboardItemController.Create` |
| 4 | `!await _repository.ValidateParentIdAsync(dto.parent_id` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/KikobaDashboardItemController.cs › KikobaDashboardItemController.Create` |
| 5 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/KikobaDashboardItemController.cs › KikobaDashboardItemController.Create` |
| 6 | `excludeId.HasValue` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/KikobaDashboardItemController.cs › KikobaDashboardItemController.Create` |
| 7 | `!parentId.HasValue` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/KikobaDashboardItemController.cs › KikobaDashboardItemController.Create` |
| 8 | `!parentExists` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/KikobaDashboardItemController.cs › KikobaDashboardItemController.Create` |
| 9 | `excludeId.HasValue` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/KikobaDashboardItemController.cs › KikobaDashboardItemController.Create` |
| 10 | `IsDescendant(allItems, excludeId.Value, parentId.Value` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/KikobaDashboardItemController.cs › KikobaDashboardItemController.Create` |

## Internal call chain
1. Client POST `/api/KikobaDashboardItem/create`.
2. `KikobaDashboardItemController.Create` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/KikobaDashboardItemController.cs`).
3. Calls `_logger.LogDebug`.
4. Calls `MethodBase.GetCurrentMethod`.
5. Calls `MethodBase.GetCurrentMethod`.
6. Calls `string.IsNullOrEmpty`.
7. Calls `string.IsNullOrEmpty`.
8. Calls `_repository.FlowIdExistsAsync`.
9. Calls `_repository.ValidateParentIdAsync`.
10. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>KikobaDashboardItemController: POST /api/KikobaDashboardItem/create
  participant KikobaDashboardItemController
  KikobaDashboardItemController->>_logger: LogDebug()
  KikobaDashboardItemController->>MethodBase: GetCurrentMethod()
  KikobaDashboardItemController->>dto: ToString()
  KikobaDashboardItemController->>string: IsNullOrEmpty()
  KikobaDashboardItemController->>_repository: FlowIdExistsAsync()
  KikobaDashboardItemController->>_repository: ValidateParentIdAsync()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/KikobaDashboardItemController.cs › KikobaDashboardItemController.Create` @ `9c00072`
- Decrypted DTO `KikobaDashboardItemDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
