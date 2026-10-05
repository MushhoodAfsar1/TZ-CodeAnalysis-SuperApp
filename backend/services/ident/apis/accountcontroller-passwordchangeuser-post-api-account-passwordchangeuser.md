---
kb_section: backend
type: api-contract
ids: [BE-API-IDENT-023]
service: IDENT
repo: TZ-Tigo-SuperApp-Identity
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: e7397b0
updated: 2026-10-05
confidence: confirmed
---
# BE-API-IDENT-023 AccountController.passwordchangeuser
**Service:** BE-SVC-IDENT · **Handler:** `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.passwordchangeuser` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Account/passwordchangeuser
  internal_path: /api/Account/passwordchangeuser
  dispatch_field: null
  dispatch_value: null
  controller_action: AccountController.passwordchangeuser
  topic: null
```

## Exposure & security
- **Auth:** anonymous
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| FirstName | `string` | no | — | DataAnnotations / action | — |
| LastName | `string` | no | — | DataAnnotations / action | — |
| FullName | `string` | no | — | DataAnnotations / action | — |
| Email | `string` | no | — | DataAnnotations / action | — |
| Password | `string?` | no | — | DataAnnotations / action | — |
| MobileNo | `string` | no | — | DataAnnotations / action | — |
| UserName | `string` | no | — | DataAnnotations / action | — |
| JobTitle | `string?` | no | — | DataAnnotations / action | — |
| Department | `string?` | no | — | DataAnnotations / action | — |
| IsFirstLogin | `bool` | no | — | DataAnnotations / action | — |
| ExpiryTime | `DateTime?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "FirstName": "<FirstName>", "LastName": "<LastName>", "FullName": "<FullName>", "Email": "<Email>", "Password": "<Password>", "MobileNo": "<MobileNo>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | AuthorizationFilter claim `AccountController:passwordchangeuser` or role Admin | 400 no permission | BE-BR-IDENT-001 | `Filter/AuthorizationFilter.cs › OnActionExecuting` |
| 2 | Guard: User did not exists | HTTP 200-envelope | — | `TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.passwordchangeuser` |
| 3 | Guard: Password changed | HTTP 200-envelope | — | `TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.passwordchangeuser` |
| 4 | Guard: password not changed | HTTP 200-envelope | — | `TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.passwordchangeuser` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `AccountController.passwordchangeuser`
2. Action body in `TZTigoSuperAppIdentity/Controllers/AccountController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as AccountController
  participant Svc as downstream
  App->>Ctrl: POST /api/Account/passwordchangeuser
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
| — | 200-envelope | — | success=false envelope | User did not exists | no |
| — | 200-envelope | — | success=false envelope | Password changed | no |
| — | 200-envelope | — | success=false envelope | password not changed | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/ident/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.passwordchangeuser` @ `e7397b0`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
