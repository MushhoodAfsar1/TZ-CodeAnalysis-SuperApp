---
kb_section: backend
type: api-contract
ids: [BE-API-IDENT-008]
service: IDENT
repo: TZ-Tigo-SuperApp-Identity
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: e7397b0
updated: 2026-10-05
confidence: confirmed
---

# BE-API-IDENT-008 MenuController.add
**Service:** BE-SVC-IDENT · **Handler:** `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/MenuController.cs › MenuController.add` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Menu/add
  internal_path: /api/Menu/add
  dispatch_field: null
  dispatch_value: null
  controller_action: MenuController.add
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Menu/add`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `id` | `int` | N | — | shape only | id |
| `lable` | `string` | N | — | shape only | lable |
| `permission_type` | `string` | N | — | shape only | permission_type |
| `icon` | `string` | N | — | shape only | icon |
| `router_link` | `string` | N | — | shape only | router_link |
| `controller` | `string` | N | — | shape only | controller |
| `parent_id` | `int` | N | — | shape only | parent_id |
| `is_active` | `bool` | N | — | shape only | is_active |
| `order` | `int` | N | — | shape only | order |

Headers / route / query params: none parsed beyond action signature `[('menu', 'MenuDto')]`

Sample (synthetic):
```json
{
  "id": 0,
  "lable": "<string>",
  "permission_type": "<string>",
  "icon": "<string>",
  "router_link": "<string>",
  "controller": "<string>",
  "parent_id": 0,
  "is_active": false,
  "order": 0
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `_configuration.GetValue<string>("EnableLog:Information"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/MenuController.cs › MenuController.add` |
| 2 | `param is string` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/MenuController.cs › MenuController.add` |
| 3 | `_configuration.GetValue<string>("EnableLog:Error"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/MenuController.cs › MenuController.add` |

## Internal call chain
1. Client POST `/api/Menu/add`.
2. `MenuController.add` runs (`TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/MenuController.cs`).
3. Calls `JsonConvert.SerializeObject`.
4. Calls `User.FindFirst`.
5. Calls `Menu.AddAsync`.
6. Calls `_unitOfWork.Save`.
7. Calls `JsonConvert.SerializeObject`.
8. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>MenuController: POST /api/Menu/add
  participant MenuController
  MenuController->>_logger: LogInformation()
  MenuController->>User: FindFirst()
  MenuController->>Value: ToString()
  MenuController->>Menu: AddAsync()
  MenuController->>_unitOfWork: Save()
  MenuController->>_logger: LogError()
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
- `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/MenuController.cs › MenuController.add` @ `e7397b0`
- Decrypted DTO `MenuDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
