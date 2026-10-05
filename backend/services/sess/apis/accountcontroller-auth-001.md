---
kb_section: backend
type: api-contract
ids: [BE-API-SESS-001]
service: SESS
repo: TZ-Tigo-SuperApp-Session
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 6f24061
updated: 2026-10-05
confidence: confirmed
---

# BE-API-SESS-001 AccountController.Auth
**Service:** BE-SVC-SESS · **Handler:** `TZ-Tigo-SuperApp-Session/TZTigoSuperAppSession/Controllers/AccountController.cs › AccountController.Auth` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Account/auth
  internal_path: /api/Account/auth
  dispatch_field: null
  dispatch_value: null
  controller_action: AccountController.Auth
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Account/auth`
- **Auth / filters:** none on action (pipeline may still authorize)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `msisdn` | `string?` | Y | — | [Required] | msisdn |
| `deviceid` | `string?` | N | — | shape only | deviceid |

Headers / route / query params: none parsed beyond action signature `[('request', 'TokenDto')]`

Sample (synthetic):
```json
{
  "msisdn": "255XXXXXXXXX",
  "deviceid": "<device-id>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `!validMsisdn` | branch / error envelope | — | `TZ-Tigo-SuperApp-Session/TZTigoSuperAppSession/Controllers/AccountController.cs › AccountController.Auth` |
| 2 | `_configuration.GetValue<string>("EnableLog:Information"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Session/TZTigoSuperAppSession/Controllers/AccountController.cs › AccountController.Auth` |
| 3 | `_configuration.GetValue<string>("EnableLog:Information"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Session/TZTigoSuperAppSession/Controllers/AccountController.cs › AccountController.Auth` |
| 4 | `_configuration.GetValue<string>("EnableLog:Information"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Session/TZTigoSuperAppSession/Controllers/AccountController.cs › AccountController.Auth` |
| 5 | `_configuration.GetValue<string>("EnableLog:Information"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Session/TZTigoSuperAppSession/Controllers/AccountController.cs › AccountController.Auth` |
| 6 | `_configuration.GetValue<string>("EnableLog:Information"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Session/TZTigoSuperAppSession/Controllers/AccountController.cs › AccountController.Auth` |
| 7 | `_configuration.GetValue<string>("EnableLog:Information"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Session/TZTigoSuperAppSession/Controllers/AccountController.cs › AccountController.Auth` |

## Internal call chain
1. Client POST `/api/Account/auth`.
2. `AccountController.Auth` runs (`TZ-Tigo-SuperApp-Session/TZTigoSuperAppSession/Controllers/AccountController.cs`).
3. Calls `JsonConvert.SerializeObject`.
4. Calls `profileService.CheckAuthenticationAsync`.
5. Calls `Now.AddSeconds`.
6. Calls `Convert.ToInt32`.
7. Calls `_configuration.GetSection`.
8. Calls `Convert.ToInt32`.
9. Calls `_configuration.GetSection`.
10. Calls `Now.AddSeconds`.
11. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>AccountController: POST /api/Account/auth
  participant AccountController
  AccountController->>_logger: LogInformation()
  AccountController->>profileService: CheckAuthenticationAsync()
  AccountController->>Now: AddSeconds()
  AccountController->>Convert: ToInt32()
  AccountController->>_configuration: GetSection()
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
| 500 | 500 | BE-ERR-SESS-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-SESS-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-SESS-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-Session/TZTigoSuperAppSession/Controllers/AccountController.cs › AccountController.Auth` @ `6f24061`
- Decrypted DTO `TokenDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
