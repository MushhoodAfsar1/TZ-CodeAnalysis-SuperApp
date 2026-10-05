---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-268]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-268 ResponseCodeController.Create
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ResponseCodeController.cs › ResponseCodeController.Create` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/ResponseCode/create
  internal_path: /api/ResponseCode/create
  dispatch_field: null
  dispatch_value: null
  controller_action: ResponseCodeController.Create
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/ResponseCode/create`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `id` | `int` | N | — | shape only | id |
| `third_party_code` | `string` | N | — | shape only | third_party_code |
| `third_party_message` | `string` | N | — | shape only | third_party_message |
| `channel` | `int` | N | — | shape only | channel |
| `response_code` | `string` | N | — | shape only | response_code |
| `service_name` | `string?` | N | — | shape only | service_name |
| `service_method_name` | `string?` | N | — | shape only | service_method_name |
| `language` | `List<SelectItem>?` | N | — | shape only | language |

Headers / route / query params: none parsed beyond action signature `[('errorcode', 'ErrorCodeDto')]`

Sample (synthetic):
```json
{
  "id": 0,
  "third_party_code": "<string>",
  "third_party_message": "<string>",
  "channel": 0,
  "response_code": "<string>",
  "service_name": "<string>",
  "service_method_name": "<string>",
  "language": []
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `!await _errorCodeRepository.ResponseExists(errorcode` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ResponseCodeController.cs › ResponseCodeController.Create` |
| 2 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ResponseCodeController.cs › ResponseCodeController.Create` |
| 3 | `result == null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ResponseCodeController.cs › ResponseCodeController.Create` |
| 4 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ResponseCodeController.cs › ResponseCodeController.Create` |
| 5 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ResponseCodeController.cs › ResponseCodeController.Create` |

## Internal call chain
1. Client POST `/api/ResponseCode/create`.
2. `ResponseCodeController.Create` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ResponseCodeController.cs`).
3. Calls `_logger.LogDebug`.
4. Calls `MethodBase.GetCurrentMethod`.
5. Calls `MethodBase.GetCurrentMethod`.
6. Calls `Diagnostics.StackFrame`.
7. Calls `_errorCodeRepository.ResponseExists`.
8. Calls `User.FindFirst`.
9. Calls `_logger.LogDebug`.
10. Calls `MethodBase.GetCurrentMethod`.
11. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>ResponseCodeController: POST /api/ResponseCode/create
  participant ResponseCodeController
  ResponseCodeController->>_logger: LogDebug()
  ResponseCodeController->>MethodBase: GetCurrentMethod()
  ResponseCodeController->>errorcode: ToString()
  ResponseCodeController->>Diagnostics: StackFrame()
  ResponseCodeController->>_errorCodeRepository: ResponseExists()
  ResponseCodeController->>User: FindFirst()
  ResponseCodeController->>Value: ToString()
  ResponseCodeController->>mapped: ToString()
  ResponseCodeController->>Utilities: GetDateTime()
  ResponseCodeController->>_errorCodeRepository: CreateErrorCodeAsync()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ResponseCodeController.cs › ResponseCodeController.Create` @ `9c00072`
- Decrypted DTO `ErrorCodeDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
