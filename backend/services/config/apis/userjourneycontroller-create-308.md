---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-308]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-308 UserJourneyController.Create
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/UserJourneyController.cs › UserJourneyController.Create` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/UserJourney/create
  internal_path: /api/UserJourney/create
  dispatch_field: null
  dispatch_value: null
  controller_action: UserJourneyController.Create
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/UserJourney/create`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `Id` | `int` | N | — | shape only | Id |
| `FlowId` | `string` | N | — | shape only | FlowId |
| `Url` | `string` | N | — | shape only | Url |
| `Name` | `string?` | N | — | shape only | Name |
| `Size` | `string?` | N | — | shape only | Size |
| `Type` | `string?` | N | — | shape only | Type |
| `IsUrl` | `bool` | N | — | shape only | IsUrl |
| `AddedOn` | `DateTime?` | N | — | shape only | AddedOn |
| `CreatedBy` | `string?` | N | — | shape only | CreatedBy |
| `UpdatedBy` | `string?` | N | — | shape only | UpdatedBy |

Headers / route / query params: none parsed beyond action signature `[('userJourneyDto', 'UserJourneyDto')]`

Sample (synthetic):
```json
{
  "Id": 0,
  "FlowId": "<string>",
  "Url": "<string>",
  "Name": "<string>",
  "Size": "<string>",
  "Type": "<string>",
  "IsUrl": false,
  "AddedOn": "<iso-datetime>",
  "CreatedBy": "<string>",
  "UpdatedBy": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `userJourneyDto.IsUrl != true` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/UserJourneyController.cs › UserJourneyController.Create` |
| 2 | `string.IsNullOrEmpty(userJourneyDto.Url` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/UserJourneyController.cs › UserJourneyController.Create` |
| 3 | `response.success == false` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/UserJourneyController.cs › UserJourneyController.Create` |
| 4 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/UserJourneyController.cs › UserJourneyController.Create` |
| 5 | `imageSubCategoriesList != null && imageSubCategoriesList.Data != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/UserJourneyController.cs › UserJourneyController.Create` |
| 6 | `subCategoryId != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/UserJourneyController.cs › UserJourneyController.Create` |
| 7 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/UserJourneyController.cs › UserJourneyController.Create` |
| 8 | `_configuration.GetValue<string>("EnableLog:Error"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/UserJourneyController.cs › UserJourneyController.Create` |

## Internal call chain
1. Client POST `/api/UserJourney/create`.
2. `UserJourneyController.Create` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/UserJourneyController.cs`).
3. Calls `_logger.LogDebug`.
4. Calls `MethodBase.GetCurrentMethod`.
5. Calls `MethodBase.GetCurrentMethod`.
6. Calls `JsonConvert.SerializeObject`.
7. Calls `Diagnostics.StackFrame`.
8. Calls `string.IsNullOrEmpty`.
9. Calls `AudioVideoUploadHelper.Upload`.
10. Calls `_userJourneyRepository.CreateAsync`.
11. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>UserJourneyController: POST /api/UserJourney/create
  participant UserJourneyController
  UserJourneyController->>_logger: LogDebug()
  UserJourneyController->>MethodBase: GetCurrentMethod()
  UserJourneyController->>Diagnostics: StackFrame()
  UserJourneyController->>string: IsNullOrEmpty()
  UserJourneyController->>AudioVideoUploadHelper: Upload()
  UserJourneyController->>_userJourneyRepository: CreateAsync()
  UserJourneyController->>_logger: LogError()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/UserJourneyController.cs › UserJourneyController.Create` @ `9c00072`
- Decrypted DTO `UserJourneyDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
