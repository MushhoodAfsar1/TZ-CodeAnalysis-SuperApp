---
kb_section: backend
type: api-contract
ids: [BE-API-IDENT-011]
service: IDENT
repo: TZ-Tigo-SuperApp-Identity
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: e7397b0
updated: 2026-10-05
confidence: confirmed
---
# BE-API-IDENT-011 MenuController.getsubmenuall
**Service:** BE-SVC-IDENT · **Handler:** `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/MenuController.cs › MenuController.getsubmenuall` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Menu/getsubmenuall
  internal_path: /api/Menu/getsubmenuall
  dispatch_field: null
  dispatch_value: null
  controller_action: MenuController.getsubmenuall
  topic: null
```

## Exposure & security
- **Auth:** JWT
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| menu_id | `int` | yes | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "menu_id": "<menu_id>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | JWT via `X-User-Session` / Bearer | 401 | — | `TZTigoSuperAppIdentity/Controllers/MenuController.cs › MenuController` |
| 2 | Guard: data successfully fetch | HTTP 200-envelope | — | `TZTigoSuperAppIdentity/Controllers/MenuController.cs › MenuController.getsubmenuall` |
| 3 | Guard: no data found | HTTP 200-envelope | — | `TZTigoSuperAppIdentity/Controllers/MenuController.cs › MenuController.getsubmenuall` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `MenuController.getsubmenuall`
2. Action body in `TZTigoSuperAppIdentity/Controllers/MenuController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as MenuController
  participant Svc as downstream
  App->>Ctrl: POST /api/Menu/getsubmenuall
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
| See service data-model | R/W | Traced at SHA e7397b0 |

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
| — | 200-envelope | — | success=false envelope | data successfully fetch | no |
| — | 200-envelope | — | success=false envelope | no data found | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/ident/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/MenuController.cs › MenuController.getsubmenuall` @ `e7397b0`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
