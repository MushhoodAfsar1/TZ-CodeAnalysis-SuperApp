---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-083]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-083 InviteIconController.Create
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/InviteIconController.cs › InviteIconController.Create` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/InviteIcon/create
  internal_path: /api/InviteIcon/create
  dispatch_field: null
  dispatch_value: null
  controller_action: InviteIconController.Create
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
| group_id | `string` | no | — | DataAnnotations / action | — |
| icon_light | `string?` | no | — | DataAnnotations / action | — |
| icon_dark | `string?` | no | — | DataAnnotations / action | — |
| is_enabled | `bool` | no | — | DataAnnotations / action | — |
| created_by | `string?` | no | — | DataAnnotations / action | — |
| created_date | `DateTime` | no | — | DataAnnotations / action | — |
| updated_by | `string?` | no | — | DataAnnotations / action | — |
| updated_date | `DateTime?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "Id": "<Id>", "group_id": "<group_id>", "icon_light": "<icon_light>", "icon_dark": "<icon_dark>", "is_enabled": "<is_enabled>", "created_by": "<created_by>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | JWT via `X-User-Session` / Bearer | 401 | — | `TZTigoSuperAppConfiguration/Controllers/BO/InviteIconController.cs › InviteIconController` |
| 2 | Guard: Group ID is required | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/InviteIconController.cs › InviteIconController.Create` |
| 3 | Guard: Group ID already exists | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/InviteIconController.cs › InviteIconController.Create` |
| 4 | Guard: Invite icon created successfully | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/InviteIconController.cs › InviteIconController.Create` |
| 5 | Guard: An error occurred while creating the item | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/InviteIconController.cs › InviteIconController.Create` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `InviteIconController.Create`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/BO/InviteIconController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as InviteIconController
  participant Svc as downstream
  App->>Ctrl: POST /api/InviteIcon/create
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
| — | 200-envelope | — | success=false envelope | Group ID is required | no |
| — | 200-envelope | — | success=false envelope | Group ID already exists | no |
| — | 200-envelope | — | success=false envelope | Invite icon created successfully | no |
| — | 200-envelope | — | success=false envelope | An error occurred while creating the item | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/config/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/InviteIconController.cs › InviteIconController.Create` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
