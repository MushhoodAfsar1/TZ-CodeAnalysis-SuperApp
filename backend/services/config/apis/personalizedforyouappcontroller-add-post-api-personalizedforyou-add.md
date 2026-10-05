---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-384]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-384 PersonalizedForYouAppController.Add
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/PersonalizedForYouAppController.cs › PersonalizedForYouAppController.Add` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/personalizedforyou/add
  internal_path: /api/personalizedforyou/add
  dispatch_field: null
  dispatch_value: null
  controller_action: PersonalizedForYouAppController.Add
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** PersonalizedForYouAddRequest

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| id | `int?` | no | — | DataAnnotations / action | — |
| msisdn | `string?` | no | — | DataAnnotations / action | — |
| flow_id | `string?` | no | — | DataAnnotations / action | — |
| json_request | `object?` | no | — | DataAnnotations / action | — |
| itemName | `string?` | no | — | DataAnnotations / action | — |
| itemIcon | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "id": "<id>", "msisdn": "<msisdn>", "flow_id": "<flow_id>", "json_request": "<json_request>", "itemName": "<itemName>", "itemIcon": "<itemIcon>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Guard: msisdn and flow_id are required | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/AppController/PersonalizedForYouAppController.cs › PersonalizedForYouAppController.Add` |
| 2 | Guard: Saved successfully | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/AppController/PersonalizedForYouAppController.cs › PersonalizedForYouAppController.Add` |
| 3 | Guard: An error occurred | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/AppController/PersonalizedForYouAppController.cs › PersonalizedForYouAppController.Add` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `PersonalizedForYouAppController.Add`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/AppController/PersonalizedForYouAppController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as PersonalizedForYouAppController
  participant Svc as downstream
  App->>Ctrl: POST /api/personalizedforyou/add
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
| — | 200-envelope | — | success=false envelope | msisdn and flow_id are required | no |
| — | 200-envelope | — | success=false envelope | Saved successfully | no |
| — | 200-envelope | — | success=false envelope | An error occurred | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/config/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/PersonalizedForYouAppController.cs › PersonalizedForYouAppController.Add` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
