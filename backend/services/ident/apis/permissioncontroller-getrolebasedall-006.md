---
kb_section: backend
type: api-contract
ids: [BE-API-IDENT-006]
service: IDENT
repo: TZ-Tigo-SuperApp-Identity
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: e7397b0
updated: 2026-10-05
confidence: confirmed
---

# BE-API-IDENT-006 PermissionController.getrolebasedall
**Service:** BE-SVC-IDENT · **Handler:** `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/PermissionController.cs › PermissionController.getrolebasedall` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Permission/getrolebasedall
  internal_path: /api/Permission/getrolebasedall
  dispatch_field: null
  dispatch_value: null
  controller_action: PermissionController.getrolebasedall
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Permission/getrolebasedall`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| *(none parsed)* | | | | | |

Headers / route / query params: none parsed beyond action signature `[('menu_id', 'int'), ('role_id', 'string')]`

Sample (synthetic):
```json
{}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `roleclaims.FirstOrDefault(x => x.Value.ToLower(` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/PermissionController.cs › PermissionController.getrolebasedall` |
| 2 | `permissions != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/PermissionController.cs › PermissionController.getrolebasedall` |
| 3 | `_configuration.GetValue<string>("EnableLog:Information"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/PermissionController.cs › PermissionController.getrolebasedall` |
| 4 | `param is string` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/PermissionController.cs › PermissionController.getrolebasedall` |
| 5 | `filter != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/PermissionController.cs › PermissionController.getrolebasedall` |
| 6 | `includeProperties != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/PermissionController.cs › PermissionController.getrolebasedall` |
| 7 | `orderBy != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/PermissionController.cs › PermissionController.getrolebasedall` |

## Internal call chain
1. Client POST `/api/Permission/getrolebasedall`.
2. `PermissionController.getrolebasedall` runs (`TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/PermissionController.cs`).
3. Calls `Permission.GetAllAsync`.
4. Calls `Roles.FirstOrDefault`.
5. Calls `_roleManager.GetClaimsAsync`.
6. Calls `roleclaims.FirstOrDefault`.
7. Calls `Value.ToLower`.
8. Calls `permission_value.ToLower`.
9. Calls `permissionslstRoleHave.Add`.
10. Calls `permissionslstRoledont.Add`.
11. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>PermissionController: POST /api/Permission/getrolebasedall
  participant PermissionController
  PermissionController->>_logger: LogInformation()
  PermissionController->>Permission: GetAllAsync()
  PermissionController->>Roles: FirstOrDefault()
  PermissionController->>_roleManager: GetClaimsAsync()
  PermissionController->>roleclaims: FirstOrDefault()
  PermissionController->>Value: ToLower()
  PermissionController->>permission_value: ToLower()
  PermissionController->>permissionslstRoleHave: Add()
  PermissionController->>permissionslstRoledont: Add()
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
| 500 | 500 | BE-ERR-IDENT-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-IDENT-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-IDENT-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/PermissionController.cs › PermissionController.getrolebasedall` @ `e7397b0`
- Decrypted DTO `int` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
