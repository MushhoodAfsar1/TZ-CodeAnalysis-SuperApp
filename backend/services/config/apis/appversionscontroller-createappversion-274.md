---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-274]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-274 AppVersionsController.CreateAppVersion
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AppVersionsController.cs › AppVersionsController.CreateAppVersion` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/AppVersions/create-app-version
  internal_path: /api/AppVersions/create-app-version
  dispatch_field: null
  dispatch_value: null
  controller_action: AppVersionsController.CreateAppVersion
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/AppVersions/create-app-version`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `Id` | `int` | N | — | shape only | Id |
| `Version` | `string?` | N | — | shape only | Version |
| `UpdateSoft` | `bool` | N | — | shape only | UpdateSoft |
| `UpdateHard` | `bool` | N | — | shape only | UpdateHard |
| `MessageSoftUpdate` | `string?` | N | — | shape only | MessageSoftUpdate |
| `MessageHardUpdate` | `string?` | N | — | shape only | MessageHardUpdate |
| `CreatedBy` | `string?` | N | — | shape only | CreatedBy |
| `CreatedDate` | `DateTime` | N | — | shape only | CreatedDate |
| `UpdateBy` | `string?` | N | — | shape only | UpdateBy |
| `UpdatedDate` | `DateTime?` | N | — | shape only | UpdatedDate |
| `Deleted` | `bool` | N | — | shape only | Deleted |
| `AppTypeID` | `long` | N | — | shape only | AppTypeID |
| `ChannelsId` | `long` | N | — | shape only | ChannelsId |
| `CountryId` | `int` | N | — | shape only | CountryId |
| `appchannelos` | `string?` | N | — | shape only | appchannelos |
| `translationsMessages` | `List<TranslationsMessages>?` | N | — | shape only | translationsMessages |

Headers / route / query params: none parsed beyond action signature `[('appVersions', 'AppVersions')]`

Sample (synthetic):
```json
{
  "Id": 0,
  "Version": "<string>",
  "UpdateSoft": false,
  "UpdateHard": false,
  "MessageSoftUpdate": "<string>",
  "MessageHardUpdate": "<string>",
  "CreatedBy": "<string>",
  "CreatedDate": "<iso-datetime>",
  "UpdateBy": "<string>",
  "UpdatedDate": "<iso-datetime>",
  "Deleted": false,
  "AppTypeID": 0,
  "ChannelsId": 0,
  "CountryId": 0,
  "appchannelos": "<string>",
  "translationsMessages": []
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AppVersionsController.cs › AppVersionsController.CreateAppVersion` |
| 2 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AppVersionsController.cs › AppVersionsController.CreateAppVersion` |

## Internal call chain
1. Client POST `/api/AppVersions/create-app-version`.
2. `AppVersionsController.CreateAppVersion` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AppVersionsController.cs`).
3. Calls `User.FindFirst`.
4. Calls `_logger.LogDebug`.
5. Calls `MethodBase.GetCurrentMethod`.
6. Calls `MethodBase.GetCurrentMethod`.
7. Calls `Diagnostics.StackFrame`.
8. Calls `_appVersionsRepository.CreateAppVersion`.
9. Calls `_logger.LogDebug`.
10. Calls `MethodBase.GetCurrentMethod`.
11. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>AppVersionsController: POST /api/AppVersions/create-app-version
  participant AppVersionsController
  AppVersionsController->>User: FindFirst()
  AppVersionsController->>Value: ToString()
  AppVersionsController->>_logger: LogDebug()
  AppVersionsController->>MethodBase: GetCurrentMethod()
  AppVersionsController->>appVersions: ToString()
  AppVersionsController->>Diagnostics: StackFrame()
  AppVersionsController->>_appVersionsRepository: CreateAppVersion()
  AppVersionsController->>response: ToString()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AppVersionsController.cs › AppVersionsController.CreateAppVersion` @ `9c00072`
- Decrypted DTO `AppVersions` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
