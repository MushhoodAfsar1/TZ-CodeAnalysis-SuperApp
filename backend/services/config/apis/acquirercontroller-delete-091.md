---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-091]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-091 AcquirerController.Delete
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AcquirerController.cs › AcquirerController.Delete` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Acquirer/delete
  internal_path: /api/Acquirer/delete
  dispatch_field: null
  dispatch_value: null
  controller_action: AcquirerController.Delete
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Acquirer/delete`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `Id` | `Int32` | N | — | shape only | Id |
| `acquirername` | `string?` | N | — | shape only | acquirername |
| `acquirerid` | `string?` | N | — | shape only | acquirerid |
| `shortcode` | `string?` | N | — | shape only | shortcode |

Headers / route / query params: none parsed beyond action signature `[('request', 'AcquirerDto')]`

Sample (synthetic):
```json
{
  "Id": 0,
  "acquirername": "<string>",
  "acquirerid": "<string>",
  "shortcode": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AcquirerController.cs › AcquirerController.Delete` |
| 2 | `acquirerShortCode != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AcquirerController.cs › AcquirerController.Delete` |
| 3 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AcquirerController.cs › AcquirerController.Delete` |

## Internal call chain
1. Client POST `/api/Acquirer/delete`.
2. `AcquirerController.Delete` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AcquirerController.cs`).
3. Calls `User.FindFirst`.
4. Calls `_logger.LogDebug`.
5. Calls `MethodBase.GetCurrentMethod`.
6. Calls `MethodBase.GetCurrentMethod`.
7. Calls `Diagnostics.StackFrame`.
8. Calls `Utilities.GetDateTime`.
9. Calls `_acquirerRepository.DeleteAcquirerAsync`.
10. Calls `_logger.LogDebug`.
11. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>AcquirerController: POST /api/Acquirer/delete
  participant AcquirerController
  AcquirerController->>User: FindFirst()
  AcquirerController->>Value: ToString()
  AcquirerController->>_logger: LogDebug()
  AcquirerController->>MethodBase: GetCurrentMethod()
  AcquirerController->>mapped: ToString()
  AcquirerController->>Diagnostics: StackFrame()
  AcquirerController->>Utilities: GetDateTime()
  AcquirerController->>_acquirerRepository: DeleteAcquirerAsync()
  AcquirerController->>retdata: ToString()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AcquirerController.cs › AcquirerController.Delete` @ `9c00072`
- Decrypted DTO `AcquirerDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
