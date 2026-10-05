---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-242]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-242 PersonalizedForYouItemController.Update
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/PersonalizedForYouItemController.cs › PersonalizedForYouItemController.Update` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/PersonalizedForYouItem/update
  internal_path: /api/PersonalizedForYouItem/update
  dispatch_field: null
  dispatch_value: null
  controller_action: PersonalizedForYouItemController.Update
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
| flow_id | `string?` | no | — | DataAnnotations / action | — |
| name | `string?` | no | — | DataAnnotations / action | — |
| title_en | `string` | no | — | DataAnnotations / action | — |
| title_sw | `string?` | no | — | DataAnnotations / action | — |
| icon_light | `string?` | no | — | DataAnnotations / action | — |
| icon_dark | `string?` | no | — | DataAnnotations / action | — |
| is_enabled | `bool` | no | — | DataAnnotations / action | — |
| is_default | `bool` | no | — | DataAnnotations / action | — |
| created_by | `string?` | no | — | DataAnnotations / action | — |
| created_date | `DateTime` | no | — | DataAnnotations / action | — |
| updated_by | `string?` | no | — | DataAnnotations / action | — |
| updated_date | `DateTime?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "Id": "<Id>", "flow_id": "<flow_id>", "name": "<name>", "title_en": "<title_en>", "title_sw": "<title_sw>", "icon_light": "<icon_light>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | JWT via `X-User-Session` / Bearer | 401 | — | `TZTigoSuperAppConfiguration/Controllers/BO/PersonalizedForYouItemController.cs › PersonalizedForYouItemController` |
| 2 | Guard: Valid ID is required for update | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/PersonalizedForYouItemController.cs › PersonalizedForYouItemController.Update` |
| 3 | Guard: Item not found | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/PersonalizedForYouItemController.cs › PersonalizedForYouItemController.Update` |
| 4 | Guard: Title (English) is required | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/PersonalizedForYouItemController.cs › PersonalizedForYouItemController.Update` |
| 5 | Guard: Personalized for You item updated successfully | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/PersonalizedForYouItemController.cs › PersonalizedForYouItemController.Update` |
| 6 | Guard: An error occurred while updating the item | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/PersonalizedForYouItemController.cs › PersonalizedForYouItemController.Update` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `PersonalizedForYouItemController.Update`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/BO/PersonalizedForYouItemController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as PersonalizedForYouItemController
  participant Svc as downstream
  App->>Ctrl: POST /api/PersonalizedForYouItem/update
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
| — | 200-envelope | — | success=false envelope | Valid ID is required for update | no |
| — | 200-envelope | — | success=false envelope | Item not found | no |
| — | 200-envelope | — | success=false envelope | Title (English) is required | no |
| — | 200-envelope | — | success=false envelope | Personalized for You item updated successfully | no |
| — | 200-envelope | — | success=false envelope | An error occurred while updating the item | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/config/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/PersonalizedForYouItemController.cs › PersonalizedForYouItemController.Update` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
