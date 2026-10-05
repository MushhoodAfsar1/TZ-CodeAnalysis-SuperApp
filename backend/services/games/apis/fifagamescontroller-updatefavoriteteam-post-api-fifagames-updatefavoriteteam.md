---
kb_section: backend
type: api-contract
ids: [BE-API-GAMES-004]
service: GAMES
repo: TZ-Tigo-SuperApp-Games
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 10c8daa
updated: 2026-10-05
confidence: confirmed
---
# BE-API-GAMES-004 FifaGamesController.UpdateFavoriteTeam
**Service:** BE-SVC-GAMES · **Handler:** `TZ-Tigo-SuperApp-Games/TZTigoSuperAppGames/Controllers/FifaGamesController.cs › FifaGamesController.UpdateFavoriteTeam` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/FifaGames/UpdateFavoriteTeam
  internal_path: /api/FifaGames/UpdateFavoriteTeam
  dispatch_field: null
  dispatch_value: null
  controller_action: FifaGamesController.UpdateFavoriteTeam
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** UpdateFavoriteTeamRequest

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| msisdn | `string` | no | — | DataAnnotations / action | — |
| teamId | `int` | no | — | DataAnnotations / action | — |
| fifaCode | `string` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "msisdn": "<msisdn>", "teamId": "<teamId>", "fifaCode": "<fifaCode>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `FifaGamesController.UpdateFavoriteTeam`
2. Action body in `TZTigoSuperAppGames/Controllers/FifaGamesController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as FifaGamesController
  participant Svc as downstream
  App->>Ctrl: POST /api/FifaGames/UpdateFavoriteTeam
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
| See service data-model | R/W | Traced at SHA 10c8daa |

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
See `services/games/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Games/TZTigoSuperAppGames/Controllers/FifaGamesController.cs › FifaGamesController.UpdateFavoriteTeam` @ `10c8daa`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
