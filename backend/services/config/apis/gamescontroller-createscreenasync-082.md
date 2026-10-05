---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-082]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-082 GamesController.CreateScreenAsync
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/GamesController.cs › GamesController.CreateScreenAsync` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Games/screens/create
  internal_path: /api/Games/screens/create
  dispatch_field: null
  dispatch_value: null
  controller_action: GamesController.CreateScreenAsync
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Games/screens/create`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `Id` | `int` | N | — | shape only | Id |
| `screen_name` | `string?` | N | — | shape only | screen_name |
| `title_en` | `string?` | N | — | shape only | title_en |
| `title_sw` | `string?` | N | — | shape only | title_sw |
| `title_text_color` | `string?` | N | — | shape only | title_text_color |
| `bullet_points` | `List<GameBulletPointDto>?` | N | — | shape only | bullet_points |
| `logo_urls` | `List<string>?` | N | — | shape only | logo_urls |
| `logo_title_en` | `string?` | N | — | shape only | logo_title_en |
| `logo_title_sw` | `string?` | N | — | shape only | logo_title_sw |
| `logo_title_color` | `string?` | N | — | shape only | logo_title_color |
| `logo_title_font` | `int?` | N | — | shape only | logo_title_font |
| `logo_description_en` | `string?` | N | — | shape only | logo_description_en |
| `logo_description_sw` | `string?` | N | — | shape only | logo_description_sw |
| `logo_description_color` | `string?` | N | — | shape only | logo_description_color |
| `logo_description_font` | `int?` | N | — | shape only | logo_description_font |
| `overlay_urls` | `List<string>?` | N | — | shape only | overlay_urls |
| `overlay_title_en` | `string?` | N | — | shape only | overlay_title_en |
| `overlay_title_sw` | `string?` | N | — | shape only | overlay_title_sw |
| `overlay_title_color` | `string?` | N | — | shape only | overlay_title_color |
| `overlay_title_font` | `int?` | N | — | shape only | overlay_title_font |
| `overlay_description_en` | `string?` | N | — | shape only | overlay_description_en |
| `overlay_description_sw` | `string?` | N | — | shape only | overlay_description_sw |
| `overlay_description_color` | `string?` | N | — | shape only | overlay_description_color |
| `overlay_description_font` | `int?` | N | — | shape only | overlay_description_font |
| `background_urls` | `List<string>?` | N | — | shape only | background_urls |
| `background_title_en` | `string?` | N | — | shape only | background_title_en |
| `background_title_sw` | `string?` | N | — | shape only | background_title_sw |
| `background_title_color` | `string?` | N | — | shape only | background_title_color |
| `background_title_font` | `int?` | N | — | shape only | background_title_font |
| `background_description_en` | `string?` | N | — | shape only | background_description_en |
| `background_description_sw` | `string?` | N | — | shape only | background_description_sw |
| `background_description_color` | `string?` | N | — | shape only | background_description_color |
| `background_description_font` | `int?` | N | — | shape only | background_description_font |
| `foreground_urls` | `List<string>?` | N | — | shape only | foreground_urls |
| `foreground_title_en` | `string?` | N | — | shape only | foreground_title_en |
| `foreground_title_sw` | `string?` | N | — | shape only | foreground_title_sw |
| `foreground_title_color` | `string?` | N | — | shape only | foreground_title_color |
| `foreground_title_font` | `int?` | N | — | shape only | foreground_title_font |
| `foreground_description_en` | `string?` | N | — | shape only | foreground_description_en |
| `foreground_description_sw` | `string?` | N | — | shape only | foreground_description_sw |
| `foreground_description_color` | `string?` | N | — | shape only | foreground_description_color |
| `foreground_description_font` | `int?` | N | — | shape only | foreground_description_font |
| `is_active` | `bool` | N | — | shape only | is_active |
| `sort_order` | `int` | N | — | shape only | sort_order |
| `buttons` | `List<GameButtonDto>?` | N | — | shape only | buttons |

Headers / route / query params: none parsed beyond action signature `[('dto', 'GameScreenDto')]`

Sample (synthetic):
```json
{
  "Id": 0,
  "screen_name": "<string>",
  "title_en": "<string>",
  "title_sw": "<string>",
  "title_text_color": "<string>",
  "bullet_points": [],
  "logo_urls": [],
  "logo_title_en": "<string>",
  "logo_title_sw": "<string>",
  "logo_title_color": "<string>",
  "logo_title_font": 0,
  "logo_description_en": "<string>",
  "logo_description_sw": "<string>",
  "logo_description_color": "<string>",
  "logo_description_font": 0,
  "overlay_urls": [],
  "overlay_title_en": "<string>",
  "overlay_title_sw": "<string>",
  "overlay_title_color": "<string>",
  "overlay_title_font": 0,
  "overlay_description_en": "<string>",
  "overlay_description_sw": "<string>",
  "overlay_description_color": "<string>",
  "overlay_description_font": 0,
  "background_urls": []
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `existingRecord == null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/GamesController.cs › GamesController.CreateScreenAsync` |
| 2 | `_configuration.GetValue<string>("EnableLog:Error"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/GamesController.cs › GamesController.CreateScreenAsync` |

## Internal call chain
1. Client POST `/api/Games/screens/create`.
2. `GamesController.CreateScreenAsync` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/GamesController.cs`).
3. Calls `_screenRepository.GetByIdAsync`.
4. Calls `_screenRepository.DeleteAsync`.
5. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>GamesController: POST /api/Games/screens/create
  participant GamesController
  GamesController->>_screenRepository: GetByIdAsync()
  GamesController->>_screenRepository: DeleteAsync()
  GamesController->>_logger: LogError()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/GamesController.cs › GamesController.CreateScreenAsync` @ `9c00072`
- Decrypted DTO `GameScreenDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
