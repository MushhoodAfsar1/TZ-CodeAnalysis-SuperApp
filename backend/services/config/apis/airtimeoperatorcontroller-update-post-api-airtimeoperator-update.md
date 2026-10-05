---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-162]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-162 AirtimeOperatorController.Update
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AirtimeOperatorController.cs › AirtimeOperatorController.Update` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/AirtimeOperator/Update
  internal_path: /api/AirtimeOperator/Update
  dispatch_field: null
  dispatch_value: null
  controller_action: AirtimeOperatorController.Update
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| id | `int?` | no | — | DataAnnotations / action | — |
| operatorName | `string?` | no | — | DataAnnotations / action | — |
| businessNumber | `string?` | no | — | DataAnnotations / action | — |
| brand | `string?` | no | — | DataAnnotations / action | — |
| shortcode | `string?` | no | — | DataAnnotations / action | — |
| prefixes | `string?` | no | — | DataAnnotations / action | — |
| darkiconUrl | `string?` | no | — | DataAnnotations / action | — |
| lighticonUrl | `string?` | no | — | DataAnnotations / action | — |
| minimumAmount | `decimal` | no | — | DataAnnotations / action | — |
| maximumAmount | `decimal` | no | — | DataAnnotations / action | — |
| disabledMessage | `string?` | no | — | DataAnnotations / action | — |
| isdisabled | `bool` | no | — | DataAnnotations / action | — |
| image_url | `string?` | no | — | DataAnnotations / action | — |
| lightimage_url | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "id": "<id>", "operatorName": "<operatorName>", "businessNumber": "<businessNumber>", "brand": "<brand>", "shortcode": "<shortcode>", "prefixes": "<prefixes>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Guard: Some error occurred | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/AirtimeOperatorController.cs › AirtimeOperatorController.Update` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `AirtimeOperatorController.Update`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/BO/AirtimeOperatorController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as AirtimeOperatorController
  participant Svc as downstream
  App->>Ctrl: POST /api/AirtimeOperator/Update
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
| — | 200-envelope | — | success=false envelope | Some error occurred | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/config/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AirtimeOperatorController.cs › AirtimeOperatorController.Update` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
