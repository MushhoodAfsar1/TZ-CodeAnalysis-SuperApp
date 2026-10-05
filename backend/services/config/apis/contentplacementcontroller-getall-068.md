---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-068]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: partial
---

# BE-API-CONFIG-068 ContentPlacementController.GetAll
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ContentPlacementController.cs › ContentPlacementController.GetAll` · **Conf.:** partial

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/ContentPlacement/getall
  internal_path: /api/ContentPlacement/getall
  dispatch_field: null
  dispatch_value: null
  controller_action: ContentPlacementController.GetAll
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/ContentPlacement/getall`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| *(none parsed)* | | | | | |

Headers / route / query params: none parsed beyond action signature (no params).

Sample (synthetic):
```json
{}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `imageSubCategoryList != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ContentPlacementController.cs › ContentPlacementController.GetAll` |
| 2 | `imageCategory == null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ContentPlacementController.cs › ContentPlacementController.GetAll` |
| 3 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ContentPlacementController.cs › ContentPlacementController.GetAll` |
| 4 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ContentPlacementController.cs › ContentPlacementController.GetAll` |

## Internal call chain
1. Client POST `/api/ContentPlacement/getall`.
2. `ContentPlacementController.GetAll` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ContentPlacementController.cs`).
3. Calls `_repository.GetAllAsync`.
4. Calls `_logger.LogDebug`.
5. Calls `MethodBase.GetCurrentMethod`.
6. Calls `MethodBase.GetCurrentMethod`.
7. Calls `Diagnostics.StackFrame`.
8. Calls `_logger.LogDebug`.
9. Calls `string.Format`.
10. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>ContentPlacementController: POST /api/ContentPlacement/getall
  participant ContentPlacementController
  ContentPlacementController->>_repository: GetAllAsync()
  ContentPlacementController->>_logger: LogDebug()
  ContentPlacementController->>MethodBase: GetCurrentMethod()
  ContentPlacementController->>retdata: ToString()
  ContentPlacementController->>Diagnostics: StackFrame()
  ContentPlacementController->>string: Format()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ContentPlacementController.cs › ContentPlacementController.GetAll` @ `9c00072`

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
