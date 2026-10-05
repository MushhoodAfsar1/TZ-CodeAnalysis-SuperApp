---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-181]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-181 ConfigController.Update
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ConfigController.cs › ConfigController.Update` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Config/update
  internal_path: /api/Config/update
  dispatch_field: null
  dispatch_value: null
  controller_action: ConfigController.Update
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Config/update`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `id` | `int` | N | — | shape only | id |
| `configurations_country` | `int` | N | — | shape only | configurations_country |
| `configurations_channel` | `int` | N | — | shape only | configurations_channel |
| `configurations_app_channel_os` | `int` | N | — | shape only | configurations_app_channel_os |
| `config_name` | `string` | N | — | shape only | config_name |
| `config_description` | `string` | N | — | shape only | config_description |
| `config_value` | `string` | N | — | shape only | config_value |

Headers / route / query params: none parsed beyond action signature `[('obj', 'ConfigurationDto')]`

Sample (synthetic):
```json
{
  "id": 0,
  "configurations_country": 0,
  "configurations_channel": 0,
  "configurations_app_channel_os": 0,
  "config_name": "<string>",
  "config_description": "<string>",
  "config_value": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `!await _configurationRepository.ConfigExists(obj` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ConfigController.cs › ConfigController.Update` |
| 2 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ConfigController.cs › ConfigController.Update` |
| 3 | `config == null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ConfigController.cs › ConfigController.Update` |
| 4 | `config.id != obj.id` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ConfigController.cs › ConfigController.Update` |
| 5 | `config != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ConfigController.cs › ConfigController.Update` |
| 6 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ConfigController.cs › ConfigController.Update` |

## Internal call chain
1. Client POST `/api/Config/update`.
2. `ConfigController.Update` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ConfigController.cs`).
3. Calls `_logger.LogDebug`.
4. Calls `MethodBase.GetCurrentMethod`.
5. Calls `MethodBase.GetCurrentMethod`.
6. Calls `Diagnostics.StackFrame`.
7. Calls `_configurationRepository.ConfigExists`.
8. Calls `User.FindFirst`.
9. Calls `Utilities.GetDateTime`.
10. Calls `_configurationRepository.UpdateConfigurationAsync`.
11. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>ConfigController: POST /api/Config/update
  participant ConfigController
  ConfigController->>_logger: LogDebug()
  ConfigController->>MethodBase: GetCurrentMethod()
  ConfigController->>obj: ToString()
  ConfigController->>Diagnostics: StackFrame()
  ConfigController->>_configurationRepository: ConfigExists()
  ConfigController->>User: FindFirst()
  ConfigController->>Value: ToString()
  ConfigController->>Utilities: GetDateTime()
  ConfigController->>_configurationRepository: UpdateConfigurationAsync()
  ConfigController->>retdata: ToString()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ConfigController.cs › ConfigController.Update` @ `9c00072`
- Decrypted DTO `ConfigurationDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
