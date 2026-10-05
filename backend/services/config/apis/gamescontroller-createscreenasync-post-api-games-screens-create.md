---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-024]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-024 GamesController.CreateScreenAsync
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
- **Auth:** JWT
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| Id | `int` | no | — | DataAnnotations / action | — |
| screen_name | `string?` | no | — | DataAnnotations / action | — |
| title_en | `string?` | no | — | DataAnnotations / action | — |
| title_sw | `string?` | no | — | DataAnnotations / action | — |
| title_text_color | `string?` | no | — | DataAnnotations / action | — |
| bullet_points | `List<GameBulletPointDto>?` | no | — | DataAnnotations / action | — |
| logo_urls | `List<string>?` | no | — | DataAnnotations / action | — |
| logo_title_en | `string?` | no | — | DataAnnotations / action | — |
| logo_title_sw | `string?` | no | — | DataAnnotations / action | — |
| logo_title_color | `string?` | no | — | DataAnnotations / action | — |
| logo_title_font | `int?` | no | — | DataAnnotations / action | — |
| logo_description_en | `string?` | no | — | DataAnnotations / action | — |
| logo_description_sw | `string?` | no | — | DataAnnotations / action | — |
| logo_description_color | `string?` | no | — | DataAnnotations / action | — |
| logo_description_font | `int?` | no | — | DataAnnotations / action | — |
| overlay_urls | `List<string>?` | no | — | DataAnnotations / action | — |
| overlay_title_en | `string?` | no | — | DataAnnotations / action | — |
| overlay_title_sw | `string?` | no | — | DataAnnotations / action | — |
| overlay_title_color | `string?` | no | — | DataAnnotations / action | — |
| overlay_title_font | `int?` | no | — | DataAnnotations / action | — |
| overlay_description_en | `string?` | no | — | DataAnnotations / action | — |
| overlay_description_sw | `string?` | no | — | DataAnnotations / action | — |
| overlay_description_color | `string?` | no | — | DataAnnotations / action | — |
| overlay_description_font | `int?` | no | — | DataAnnotations / action | — |
| background_urls | `List<string>?` | no | — | DataAnnotations / action | — |
| background_title_en | `string?` | no | — | DataAnnotations / action | — |
| background_title_sw | `string?` | no | — | DataAnnotations / action | — |
| background_title_color | `string?` | no | — | DataAnnotations / action | — |
| background_title_font | `int?` | no | — | DataAnnotations / action | — |
| background_description_en | `string?` | no | — | DataAnnotations / action | — |
| background_description_sw | `string?` | no | — | DataAnnotations / action | — |
| background_description_color | `string?` | no | — | DataAnnotations / action | — |
| background_description_font | `int?` | no | — | DataAnnotations / action | — |
| foreground_urls | `List<string>?` | no | — | DataAnnotations / action | — |
| foreground_title_en | `string?` | no | — | DataAnnotations / action | — |
| foreground_title_sw | `string?` | no | — | DataAnnotations / action | — |
| foreground_title_color | `string?` | no | — | DataAnnotations / action | — |
| foreground_title_font | `int?` | no | — | DataAnnotations / action | — |
| foreground_description_en | `string?` | no | — | DataAnnotations / action | — |
| foreground_description_sw | `string?` | no | — | DataAnnotations / action | — |
| foreground_description_color | `string?` | no | — | DataAnnotations / action | — |
| foreground_description_font | `int?` | no | — | DataAnnotations / action | — |
| is_active | `bool` | no | — | DataAnnotations / action | — |
| sort_order | `int` | no | — | DataAnnotations / action | — |
| buttons | `List<GameButtonDto>?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "Id": "<Id>", "screen_name": "<screen_name>", "title_en": "<title_en>", "title_sw": "<title_sw>", "title_text_color": "<title_text_color>", "bullet_points": "<bullet_points>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | JWT via `X-User-Session` / Bearer | 401 | — | `TZTigoSuperAppConfiguration/Controllers/BO/GamesController.cs › GamesController` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `GamesController.CreateScreenAsync`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/BO/GamesController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as GamesController
  participant Svc as downstream
  App->>Ctrl: POST /api/Games/screens/create
  Ctrl->>Svc: business calls
  Svc-->>Ctrl: result
  Ctrl-->>App: envelope
```

## Downstream
| Order | Target (BE-API / BE-INT / BE-EVT) | Sync/Async | Condition | Sent / used fields |
|---|---|---|---|---|
| 1 | In-process services / EF / cache | Sync | always | see call chain |

## Data touched
| Entity / table / SP | R/W | Notes |
|---|---|---|
| See service data-model | R/W | Traced at SHA 9c00072 |

## Response (decrypted)
| Field (JSON) | Type | Always / when | Meaning |
|---|---|---|---|
| success | bool | typical | Operation flag |
| responseCode / responseMessage_* | string | typical | Envelope |
| Data / responseData | object | on success | Payload |

Sample (synthetic):
```json
{ "success": true, "responseCode": "00", "Data": {} }
```

## Errors
| BE code | HTTP | ID | Condition | Message key/text | Retryable |
|---|---|---|---|---|---|
| — | 500 | — | Unhandled exception | Internal error | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/config/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/GamesController.cs › GamesController.CreateScreenAsync` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
