---
kb_section: backend
type: api-contract
ids: [BE-API-IDENT-029]
service: IDENT
repo: TZ-Tigo-SuperApp-Identity
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: e7397b0
updated: 2026-10-05
confidence: confirmed
---

# BE-API-IDENT-029 AccountController.userroles
**Service:** BE-SVC-IDENT · **Handler:** `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.userroles` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Account/userroles
  internal_path: /api/Account/userroles
  dispatch_field: null
  dispatch_value: null
  controller_action: AccountController.userroles
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Account/userroles`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `FirstName` | `string` | N | — | shape only | FirstName |
| `LastName` | `string` | N | — | shape only | LastName |
| `FullName` | `string` | N | — | shape only | FullName |
| `Email` | `string` | N | — | shape only | Email |
| `Password` | `string?` | N | — | shape only | Password |
| `MobileNo` | `string` | N | — | shape only | MobileNo |
| `UserName` | `string` | N | — | shape only | UserName |
| `JobTitle` | `string?` | N | — | shape only | JobTitle |
| `Department` | `string?` | N | — | shape only | Department |
| `IsFirstLogin` | `bool` | N | — | shape only | IsFirstLogin |
| `ExpiryTime` | `DateTime?` | N | — | shape only | ExpiryTime |

Headers / route / query params: none parsed beyond action signature `[('updatedata', 'RegisterRequestDto')]`

Sample (synthetic):
```json
{
  "FirstName": "<string>",
  "LastName": "<string>",
  "FullName": "<string>",
  "Email": "user@example.com",
  "Password": "<password>",
  "MobileNo": "<string>",
  "UserName": "<string>",
  "JobTitle": "<string>",
  "Department": "<string>",
  "IsFirstLogin": false,
  "ExpiryTime": "<iso-datetime>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `userData == null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.userroles` |
| 2 | `vm != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.userroles` |
| 3 | `_configuration.GetValue<string>("EnableLog:Information"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.userroles` |
| 4 | `param is string` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.userroles` |

## Internal call chain
1. Client POST `/api/Account/userroles`.
2. `AccountController.userroles` runs (`TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs`).
3. Calls `JsonConvert.SerializeObject`.
4. Calls `_userManager.FindByEmailAsync`.
5. Calls `Roles.ToList`.
6. Calls `_userManager.GetRolesAsync`.
7. Calls `rolename.Add`.
8. Calls `roles.Where`.
9. Calls `rolename.Contains`.
10. Calls `roles.Where`.
11. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>AccountController: POST /api/Account/userroles
  participant AccountController
  AccountController->>_logger: LogInformation()
  AccountController->>_userManager: FindByEmailAsync()
  AccountController->>Roles: ToList()
  AccountController->>_userManager: GetRolesAsync()
  AccountController->>rolename: Add()
  AccountController->>roles: Where()
  AccountController->>rolename: Contains()
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
- `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.userroles` @ `e7397b0`
- Decrypted DTO `RegisterRequestDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
