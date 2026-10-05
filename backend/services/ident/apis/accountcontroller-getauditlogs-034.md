---
kb_section: backend
type: api-contract
ids: [BE-API-IDENT-034]
service: IDENT
repo: TZ-Tigo-SuperApp-Identity
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: e7397b0
updated: 2026-10-05
confidence: confirmed
---

# BE-API-IDENT-034 AccountController.getAuditLogs
**Service:** BE-SVC-IDENT · **Handler:** `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.getAuditLogs` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Account/getAuditLogs
  internal_path: /api/Account/getAuditLogs
  dispatch_field: null
  dispatch_value: null
  controller_action: AccountController.getAuditLogs
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Account/getAuditLogs`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `DateStart` | `DateOnly?` | N | — | shape only | DateStart |
| `DateFrom` | `DateOnly?` | N | — | shape only | DateFrom |
| `MenuType` | `string?` | N | — | shape only | MenuType |
| `ActionType` | `string?` | N | — | shape only | ActionType |
| `SearchText` | `string?` | N | — | shape only | SearchText |
| `PageNo` | `int?` | N | — | shape only | PageNo |
| `PageSize` | `int?` | N | — | shape only | PageSize |
| `SortField` | `string?` | N | — | shape only | SortField |
| `SortOrder` | `int?` | N | — | shape only | SortOrder |

Headers / route / query params: none parsed beyond action signature `[('request', 'FilterDTO')]`

Sample (synthetic):
```json
{
  "DateStart": "<string>",
  "DateFrom": "<string>",
  "MenuType": "<string>",
  "ActionType": "<string>",
  "SearchText": "<string>",
  "PageNo": 0,
  "PageSize": 0,
  "SortField": "<string>",
  "SortOrder": 0
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `_configuration.GetValue<string>("EnableLog:Information"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.getAuditLogs` |
| 2 | `param is string` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.getAuditLogs` |

## Internal call chain
1. Client POST `/api/Account/getAuditLogs`.
2. `AccountController.getAuditLogs` runs (`TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs`).
3. Calls `JsonConvert.SerializeObject`.
4. Calls `AuditLogs.ToListAsync`.
5. Calls `Users.ToListAsync`.
6. Calls `UserRoles.ToListAsync`.
7. Calls `Roles.ToListAsync`.
8. Calls `string.Join`.
9. Calls `userRoleMap.ContainsKey`.
10. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>AccountController: POST /api/Account/getAuditLogs
  participant AccountController
  AccountController->>_logger: LogInformation()
  AccountController->>AuditLogs: ToListAsync()
  AccountController->>Users: ToListAsync()
  AccountController->>UserRoles: ToListAsync()
  AccountController->>Roles: ToListAsync()
  AccountController->>string: Join()
  AccountController->>userRoleMap: ContainsKey()
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
- `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.getAuditLogs` @ `e7397b0`
- Decrypted DTO `FilterDTO` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
