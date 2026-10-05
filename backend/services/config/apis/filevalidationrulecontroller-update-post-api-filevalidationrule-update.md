---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-031]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-031 FileValidationRuleController.Update
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/FileValidationRuleController.cs › FileValidationRuleController.Update` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/FileValidationRule/update
  internal_path: /api/FileValidationRule/update
  dispatch_field: null
  dispatch_value: null
  controller_action: FileValidationRuleController.Update
  topic: null
```

## Exposure & security
- **Auth:** JWT
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| id | `int` | no | — | DataAnnotations / action | — |
| category | `string` | no; max 100 | — | DataAnnotations / action | — |
| allowed_formats | `string` | no; max 500 | — | DataAnnotations / action | — |
| max_file_size_kb | `int` | no | — | DataAnnotations / action | — |
| validation_type | `string` | no; max 20 | — | DataAnnotations / action | — |
| description | `string?` | no; max 500 | — | DataAnnotations / action | — |
| notes | `string?` | no; max 500 | — | DataAnnotations / action | — |
| isactive | `bool` | no | — | DataAnnotations / action | — |
| id | `int` | no | — | DataAnnotations / action | — |
| category | `string` | no | — | DataAnnotations / action | — |
| allowed_formats | `string` | no | — | DataAnnotations / action | — |
| max_file_size_kb | `int` | no | — | DataAnnotations / action | — |
| validation_type | `string` | no | — | DataAnnotations / action | — |
| description | `string?` | no | — | DataAnnotations / action | — |
| notes | `string?` | no | — | DataAnnotations / action | — |
| isactive | `bool` | no | — | DataAnnotations / action | — |
| createdby | `string` | no | — | DataAnnotations / action | — |
| createddate | `DateTime` | no | — | DataAnnotations / action | — |
| updatedby | `string?` | no | — | DataAnnotations / action | — |
| updateddate | `DateTime?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "id": "<id>", "category": "<category>", "allowed_formats": "<allowed_formats>", "max_file_size_kb": "<max_file_size_kb>", "validation_type": "<validation_type>", "description": "<description>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | JWT via `X-User-Session` / Bearer | 401 | — | `TZTigoSuperAppConfiguration/Controllers/BO/FileValidationRuleController.cs › FileValidationRuleController` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `FileValidationRuleController.Update`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/BO/FileValidationRuleController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as FileValidationRuleController
  participant Svc as downstream
  App->>Ctrl: POST /api/FileValidationRule/update
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/FileValidationRuleController.cs › FileValidationRuleController.Update` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
