---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-141]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-141 LeaderboardController.SaveCampaignStatus
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/LeaderboardController.cs › LeaderboardController.SaveCampaignStatus` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Leaderboard/campaignstatus/save
  internal_path: /api/Leaderboard/campaignstatus/save
  dispatch_field: null
  dispatch_value: null
  controller_action: LeaderboardController.SaveCampaignStatus
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Leaderboard/campaignstatus/save`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `Id` | `int` | N | — | shape only | Id |
| `is_enabled` | `bool` | N | — | shape only | is_enabled |
| `heading_en` | `string?` | N | — | shape only | heading_en |
| `heading_sw` | `string?` | N | — | shape only | heading_sw |
| `heading_color` | `string?` | N | — | shape only | heading_color |
| `information_points` | `List<LeaderboardTextPointDto>?` | N | — | shape only | information_points |
| `background_urls` | `List<string>?` | N | — | shape only | background_urls |
| `back_button_text_en` | `string?` | N | — | shape only | back_button_text_en |
| `back_button_text_sw` | `string?` | N | — | shape only | back_button_text_sw |
| `back_button_text_color` | `string?` | N | — | shape only | back_button_text_color |
| `back_button_background_color` | `string?` | N | — | shape only | back_button_background_color |

Headers / route / query params: none parsed beyond action signature `[('dto', 'LeaderboardCampaignStatusDto')]`

Sample (synthetic):
```json
{
  "Id": 0,
  "is_enabled": false,
  "heading_en": "<string>",
  "heading_sw": "<string>",
  "heading_color": "<string>",
  "information_points": [],
  "background_urls": [],
  "back_button_text_en": "<string>",
  "back_button_text_sw": "<string>",
  "back_button_text_color": "<string>",
  "back_button_background_color": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | No explicit guard parsed in action body | — | — | static parse |

## Internal call chain
1. Client POST `/api/Leaderboard/campaignstatus/save`.
2. `LeaderboardController.SaveCampaignStatus` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/LeaderboardController.cs`).
3. Calls `_repo.GetCampaignStatusAsync`.
4. Calls `_repo.SaveCampaignStatusAsync`.
5. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>LeaderboardController: POST /api/Leaderboard/campaignstatus/save
  participant LeaderboardController
  LeaderboardController->>_repo: GetCampaignStatusAsync()
  LeaderboardController->>_repo: SaveCampaignStatusAsync()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/LeaderboardController.cs › LeaderboardController.SaveCampaignStatus` @ `9c00072`
- Decrypted DTO `LeaderboardCampaignStatusDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
