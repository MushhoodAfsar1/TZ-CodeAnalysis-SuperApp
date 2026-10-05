---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-200]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-200 HomeCardsController.Create
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/HomeCardsController.cs › HomeCardsController.Create` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/HomeCards/create
  internal_path: /api/HomeCards/create
  dispatch_field: null
  dispatch_value: null
  controller_action: HomeCardsController.Create
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/HomeCards/create`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `Id` | `int` | N | — | shape only | Id |
| `card_id` | `string` | N | — | shape only | card_id |
| `card_type` | `string` | N | — | shape only | card_type |
| `enabled` | `bool` | N | — | shape only | enabled |
| `sort_order` | `int` | N | — | shape only | sort_order |
| `is_default` | `bool` | N | — | shape only | is_default |
| `title` | `string?` | N | — | shape only | title |
| `subtitle` | `string?` | N | — | shape only | subtitle |
| `dashboard_layout_id` | `int?` | N | — | shape only | dashboard_layout_id |
| `created_by` | `string?` | N | — | shape only | created_by |
| `created_date` | `DateTime?` | N | — | shape only | created_date |
| `updated_by` | `string?` | N | — | shape only | updated_by |
| `updated_date` | `DateTime?` | N | — | shape only | updated_date |

Headers / route / query params: none parsed beyond action signature `[('dto', 'HomeCarouselCardDto')]`

Sample (synthetic):
```json
{
  "Id": 0,
  "card_id": "<string>",
  "card_type": "<string>",
  "enabled": false,
  "sort_order": 0,
  "is_default": false,
  "title": "<string>",
  "subtitle": "<string>",
  "dashboard_layout_id": 0,
  "created_by": "<string>",
  "created_date": "<iso-datetime>",
  "updated_by": "<string>",
  "updated_date": "<iso-datetime>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `await _repository.CardIdExistsAsync(dto.card_id` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/HomeCardsController.cs › HomeCardsController.Create` |
| 2 | `await _repository.OrderExistsAsync(dto.sort_order` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/HomeCardsController.cs › HomeCardsController.Create` |
| 3 | `result.Success` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/HomeCardsController.cs › HomeCardsController.Create` |
| 4 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/HomeCardsController.cs › HomeCardsController.Create` |
| 5 | `excludeId.HasValue` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/HomeCardsController.cs › HomeCardsController.Create` |
| 6 | `excludeId.HasValue` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/HomeCardsController.cs › HomeCardsController.Create` |
| 7 | `imageSubCategoriesList != null && imageSubCategoriesList.Data != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/HomeCardsController.cs › HomeCardsController.Create` |
| 8 | `subCategoryId != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/HomeCardsController.cs › HomeCardsController.Create` |

## Internal call chain
1. Client POST `/api/HomeCards/create`.
2. `HomeCardsController.Create` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/HomeCardsController.cs`).
3. Calls `_logger.LogDebug`.
4. Calls `MethodBase.GetCurrentMethod`.
5. Calls `MethodBase.GetCurrentMethod`.
6. Calls `Diagnostics.StackFrame`.
7. Calls `_repository.CardIdExistsAsync`.
8. Calls `_repository.OrderExistsAsync`.
9. Calls `_repository.CreateAsync`.
10. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>HomeCardsController: POST /api/HomeCards/create
  participant HomeCardsController
  HomeCardsController->>_logger: LogDebug()
  HomeCardsController->>MethodBase: GetCurrentMethod()
  HomeCardsController->>dto: ToString()
  HomeCardsController->>Diagnostics: StackFrame()
  HomeCardsController->>_repository: CardIdExistsAsync()
  HomeCardsController->>_repository: OrderExistsAsync()
  HomeCardsController->>_repository: CreateAsync()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/HomeCardsController.cs › HomeCardsController.Create` @ `9c00072`
- Decrypted DTO `HomeCarouselCardDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
