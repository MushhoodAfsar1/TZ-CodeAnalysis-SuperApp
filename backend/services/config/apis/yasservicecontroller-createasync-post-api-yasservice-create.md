---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-078]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-078 YasServiceController.CreateAsync
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/YasServiceController.cs › YasServiceController.CreateAsync` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/YasService/create
  internal_path: /api/YasService/create
  dispatch_field: null
  dispatch_value: null
  controller_action: YasServiceController.CreateAsync
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
| title_en | `string` | no | — | DataAnnotations / action | — |
| title_sw | `string` | no | — | DataAnnotations / action | — |
| description | `string` | no | — | DataAnnotations / action | — |
| image_url | `string` | no | — | DataAnnotations / action | — |
| dark_image_url | `string?` | no | — | DataAnnotations / action | — |
| flow_id | `string` | no | — | DataAnnotations / action | — |
| sort_order | `int` | no | — | DataAnnotations / action | — |
| isrevamp | `bool` | no | — | DataAnnotations / action | — |
| isactive | `bool` | no | — | DataAnnotations / action | — |
| displayon | `string?` | no | — | DataAnnotations / action | — |
| image_size | `string?` | no | — | DataAnnotations / action | — |
| image_name | `string?` | no | — | DataAnnotations / action | — |
| image_type | `string?` | no | — | DataAnnotations / action | — |
| dark_image_size | `string?` | no | — | DataAnnotations / action | — |
| dark_image_name | `string?` | no | — | DataAnnotations / action | — |
| dark_image_type | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "Id": "<Id>", "title_en": "<title_en>", "title_sw": "<title_sw>", "description": "<description>", "image_url": "<image_url>", "dark_image_url": "<dark_image_url>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | JWT via `X-User-Session` / Bearer | 401 | — | `TZTigoSuperAppConfiguration/Controllers/BO/YasServiceController.cs › YasServiceController` |
| 2 | Guard: saved successfully | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/YasServiceController.cs › YasServiceController.CreateAsync` |
| 3 | Guard: some error occurred | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/YasServiceController.cs › YasServiceController.CreateAsync` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `YasServiceController.CreateAsync`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/BO/YasServiceController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as YasServiceController
  participant Svc as downstream
  App->>Ctrl: POST /api/YasService/create
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
| — | 200-envelope | — | success=false envelope | saved successfully | no |
| — | 200-envelope | — | success=false envelope | some error occurred | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/config/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/YasServiceController.cs › YasServiceController.CreateAsync` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
