---
kb_section: backend
type: api-contract
ids: [BE-API-MCHANGO-007]
service: MCHANGO
repo: TZ-Tigo-SuperApp-MChango
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 7c288ab
updated: 2026-10-05
confidence: confirmed
---

# BE-API-MCHANGO-007 ChangeAccountGroupController.GetAllAccount
**Service:** BE-SVC-MCHANGO · **Handler:** `TZ-Tigo-SuperApp-MChango/TZTigoMChangoService/Controllers/MobileControllers/ChangeAccountGroupController.cs › ChangeAccountGroupController.GetAllAccount` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: GET
  public_path: /api/web/ChangeAccountGroup/GetAllAccount
  internal_path: /api/web/ChangeAccountGroup/GetAllAccount
  dispatch_field: null
  dispatch_value: null
  controller_action: ChangeAccountGroupController.GetAllAccount
  topic: null
```

## Exposure & security
- **Method / path:** `GET /api/web/ChangeAccountGroup/GetAllAccount`
- **Auth / filters:** none on action (pipeline may still authorize)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| *(none parsed)* | | | | | |

Headers / route / query params: none parsed beyond action signature `[('search', 'string?'), ('sortBy', 'string?'), ('sortDirection', 'string?')]`

Sample (synthetic):
```json
{}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `string.IsNullOrWhiteSpace(search` | branch / error envelope | — | `TZ-Tigo-SuperApp-MChango/TZTigoMChangoService/Controllers/MobileControllers/ChangeAccountGroupController.cs › ChangeAccountGroupController.GetAllAccount` |

## Internal call chain
1. Client POST `/api/web/ChangeAccountGroup/GetAllAccount`.
2. `ChangeAccountGroupController.GetAllAccount` runs (`TZ-Tigo-SuperApp-MChango/TZTigoMChangoService/Controllers/MobileControllers/ChangeAccountGroupController.cs`).
3. Calls `string.IsNullOrWhiteSpace`.
4. Calls `string.IsNullOrWhiteSpace`.
5. Calls `_groupChangeService.GetAllAccountsAsync`.
6. Calls `_groupChangeService.GetAllAccountsAsync`.
7. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>ChangeAccountGroupController: GET /api/web/ChangeAccountGroup/GetAllAccount
  participant ChangeAccountGroupController
  ChangeAccountGroupController->>string: IsNullOrWhiteSpace()
  ChangeAccountGroupController->>_groupChangeService: GetAllAccountsAsync()
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
| 500 | 500 | BE-ERR-MCHANGO-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-MCHANGO-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-MCHANGO-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-MChango/TZTigoMChangoService/Controllers/MobileControllers/ChangeAccountGroupController.cs › ChangeAccountGroupController.GetAllAccount` @ `7c288ab`
- Decrypted DTO `string?` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
