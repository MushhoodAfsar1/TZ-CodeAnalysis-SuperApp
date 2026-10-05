---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-389]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-389 GamesAppController.GetScreenWise
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/GamesAppController.cs › GamesAppController.GetScreenWise` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/GamesApp/getScreenWise
  internal_path: /api/GamesApp/getScreenWise
  dispatch_field: null
  dispatch_value: null
  controller_action: GamesAppController.GetScreenWise
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** GamesRequest

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| screenName | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "screenName": "<screenName>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Guard: success = true, statusCode = 200, transactionStatus = "Data Fetch Successfully", responseData = data  | HTTP 200 | — | `TZTigoSuperAppConfiguration/Controllers/AppController/GamesAppController.cs › GamesAppController.GetScreenWise` |
| 2 | Guard: success = false, Data = ex.ToString(),  | HTTP 500 | — | `TZTigoSuperAppConfiguration/Controllers/AppController/GamesAppController.cs › GamesAppController.GetScreenWise` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `GamesAppController.GetScreenWise`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/AppController/GamesAppController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as GamesAppController
  participant Svc as downstream
  App->>Ctrl: POST /api/GamesApp/getScreenWise
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
| — | 200 | — | reachable return | success = true, statusCode = 200, transactionStatus = "Data Fetch Successfully", responseData = data  | no |
| — | 500 | — | reachable return | success = false, Data = ex.ToString(),  | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/config/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/GamesAppController.cs › GamesAppController.GetScreenWise` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
