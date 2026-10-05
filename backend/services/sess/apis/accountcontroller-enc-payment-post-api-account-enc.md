---
kb_section: backend
type: api-contract
ids: [BE-API-SESS-003]
service: SESS
repo: TZ-Tigo-SuperApp-Session
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 6f24061
updated: 2026-10-05
confidence: confirmed
---
# BE-API-SESS-003 AccountController.enc_payment
**Service:** BE-SVC-SESS · **Handler:** `TZ-Tigo-SuperApp-Session/TZTigoSuperAppSession/Controllers/AccountController.cs › AccountController.enc_payment` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Account/enc
  internal_path: /api/Account/enc
  dispatch_field: null
  dispatch_value: null
  controller_action: AccountController.enc_payment
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| msisdn | `string` | no | — | DataAnnotations / action | — |
| accesstoken | `string` | no | — | DataAnnotations / action | — |
| refreshtoken | `string` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "msisdn": "<msisdn>", "accesstoken": "<accesstoken>", "refreshtoken": "<refreshtoken>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `AccountController.enc_payment`
2. Action body in `TZTigoSuperAppSession/Controllers/AccountController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as AccountController
  participant Svc as downstream
  App->>Ctrl: POST /api/Account/enc
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
| See service data-model | R/W | Traced at SHA 6f24061 |

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
See `services/sess/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Session/TZTigoSuperAppSession/Controllers/AccountController.cs › AccountController.enc_payment` @ `6f24061`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
