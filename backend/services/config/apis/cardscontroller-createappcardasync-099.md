---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-099]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-099 CardsController.CreateAppCardAsync
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/CardsController.cs › CardsController.CreateAppCardAsync` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Cards/CreateAppCardAsync
  internal_path: /api/Cards/CreateAppCardAsync
  dispatch_field: null
  dispatch_value: null
  controller_action: CardsController.CreateAppCardAsync
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Cards/CreateAppCardAsync`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `id` | `int` | N | — | shape only | id |
| `imageToUpload` | `IFormFile?` | N | — | shape only | imageToUpload |
| `imgData` | `string?` | N | — | shape only | imgData |
| `name` | `string?` | N | — | shape only | name |
| `fileurl` | `string?` | N | — | shape only | fileurl |
| `filename` | `string?` | N | — | shape only | filename |
| `themetype` | `string?` | N | — | shape only | themetype |
| `themecolor` | `string?` | N | — | shape only | themecolor |

Headers / route / query params: none parsed beyond action signature `[('appCardRequest', 'CreateAppCardDto')]`

Sample (synthetic):
```json
{
  "id": 0,
  "imageToUpload": "<string>",
  "imgData": "<string>",
  "name": "<string>",
  "fileurl": "<string>",
  "filename": "<string>",
  "themetype": "<string>",
  "themecolor": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/CardsController.cs › CardsController.CreateAppCardAsync` |
| 2 | `createAppCardRequest.id > 0` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/CardsController.cs › CardsController.CreateAppCardAsync` |
| 3 | `createAppCardRequest.imgData is not null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/CardsController.cs › CardsController.CreateAppCardAsync` |
| 4 | `appCard != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/CardsController.cs › CardsController.CreateAppCardAsync` |
| 5 | `createAppCardRequest.imgData != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/CardsController.cs › CardsController.CreateAppCardAsync` |

## Internal call chain
1. Client POST `/api/Cards/CreateAppCardAsync`.
2. `CardsController.CreateAppCardAsync` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/CardsController.cs`).
3. Calls `_logger.LogDebug`.
4. Calls `MethodBase.GetCurrentMethod`.
5. Calls `MethodBase.GetCurrentMethod`.
6. Calls `JsonConvert.SerializeObject`.
7. Calls `Diagnostics.StackFrame`.
8. Calls `_appCardsRepository.CreateAppCardAsync`.
9. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>CardsController: POST /api/Cards/CreateAppCardAsync
  participant CardsController
  CardsController->>_logger: LogDebug()
  CardsController->>MethodBase: GetCurrentMethod()
  CardsController->>Diagnostics: StackFrame()
  CardsController->>_appCardsRepository: CreateAppCardAsync()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/CardsController.cs › CardsController.CreateAppCardAsync` @ `9c00072`
- Decrypted DTO `CreateAppCardDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
