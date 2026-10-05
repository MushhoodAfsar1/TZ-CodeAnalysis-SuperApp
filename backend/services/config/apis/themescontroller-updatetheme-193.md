---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-193]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-193 ThemesController.UpdateTheme
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ThemesController.cs › ThemesController.UpdateTheme` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Themes/updatetheme
  internal_path: /api/Themes/updatetheme
  dispatch_field: null
  dispatch_value: null
  controller_action: ThemesController.UpdateTheme
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Themes/updatetheme`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `id` | `int` | N | — | shape only | id |
| `categoryId` | `int` | N | — | shape only | categoryId |
| `themeName` | `string` | N | — | shape only | themeName |
| `themeBgColor` | `string` | N | — | shape only | themeBgColor |
| `themeMessage` | `string` | N | — | shape only | themeMessage |
| `themeForeground` | `string` | N | — | shape only | themeForeground |
| `imageUrl` | `string?` | N | — | shape only | imageUrl |
| `imageName` | `string?` | N | — | shape only | imageName |
| `imageSize` | `string?` | N | — | shape only | imageSize |
| `imageType` | `string?` | N | — | shape only | imageType |
| `createdBy` | `string?` | N | — | shape only | createdBy |
| `createdDate` | `DateTime?` | N | — | shape only | createdDate |
| `updatedBy` | `string?` | N | — | shape only | updatedBy |
| `updatedDate` | `DateTime?` | N | — | shape only | updatedDate |
| `isdeleted` | `string?` | N | — | shape only | isdeleted |

Headers / route / query params: none parsed beyond action signature `[('giftThemesDto', 'GiftThemesDto')]`

Sample (synthetic):
```json
{
  "id": 0,
  "categoryId": 0,
  "themeName": "<string>",
  "themeBgColor": "<string>",
  "themeMessage": "<string>",
  "themeForeground": "<string>",
  "imageUrl": "<string>",
  "imageName": "<string>",
  "imageSize": "<string>",
  "imageType": "<string>",
  "createdBy": "<string>",
  "createdDate": "<iso-datetime>",
  "updatedBy": "<string>",
  "updatedDate": "<iso-datetime>",
  "isdeleted": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `giftThemeCategoryList == null \|\| giftThemeCategoryList.Data == null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ThemesController.cs › ThemesController.UpdateTheme` |
| 2 | `item == null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ThemesController.cs › ThemesController.UpdateTheme` |
| 3 | `item.imageUrl != giftThemesDto.imageUrl` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ThemesController.cs › ThemesController.UpdateTheme` |
| 4 | `giftThemesDto.imageUrl != null && (giftThemesDto.imageUrl.Contains("data:image"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ThemesController.cs › ThemesController.UpdateTheme` |
| 5 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ThemesController.cs › ThemesController.UpdateTheme` |
| 6 | `giftThemesList != null && giftThemesList.responseData.Count > 0` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ThemesController.cs › ThemesController.UpdateTheme` |

## Internal call chain
1. Client POST `/api/Themes/updatetheme`.
2. `ThemesController.UpdateTheme` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ThemesController.cs`).
3. Calls `_logger.LogDebug`.
4. Calls `MethodBase.GetCurrentMethod`.
5. Calls `MethodBase.GetCurrentMethod`.
6. Calls `Diagnostics.StackFrame`.
7. Calls `_themesService.GetAllThemesAsync`.
8. Calls `Data.Where`.
9. Calls `imageUrl.Contains`.
10. Calls `imageUrl.Contains`.
11. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>ThemesController: POST /api/Themes/updatetheme
  participant ThemesController
  ThemesController->>_logger: LogDebug()
  ThemesController->>MethodBase: GetCurrentMethod()
  ThemesController->>Diagnostics: StackFrame()
  ThemesController->>_themesService: GetAllThemesAsync()
  ThemesController->>Data: Where()
  ThemesController->>imageUrl: Contains()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/ThemesController.cs › ThemesController.UpdateTheme` @ `9c00072`
- Decrypted DTO `GiftThemesDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
