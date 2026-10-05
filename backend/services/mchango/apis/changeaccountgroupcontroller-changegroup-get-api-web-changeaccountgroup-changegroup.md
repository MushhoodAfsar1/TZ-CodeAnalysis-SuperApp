---
kb_section: backend
type: api-contract
ids: [BE-API-MCHANGO-058]
service: MCHANGO
repo: TZ-Tigo-SuperApp-MChango
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 7c288ab
updated: 2026-10-05
confidence: confirmed
---
# BE-API-MCHANGO-058 ChangeAccountGroupController.ChangeGroup
**Service:** BE-SVC-MCHANGO · **Handler:** `TZ-Tigo-SuperApp-MChango/TZTigoMChangoService/Controllers/MobileControllers/ChangeAccountGroupController.cs › ChangeAccountGroupController.ChangeGroup` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: GET
  public_path: /api/web/ChangeAccountGroup/ChangeGroup
  internal_path: /api/web/ChangeAccountGroup/ChangeGroup
  dispatch_field: null
  dispatch_value: null
  controller_action: ChangeAccountGroupController.ChangeGroup
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| ids | `string?` | unknown | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "ids": "<ids>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Guard: transactionStatus = "No valid account IDs provided. Use comma-separated ids, e.g. ?ids=1,2,3", success = false  | HTTP 400 | — | `TZTigoMChangoService/Controllers/MobileControllers/ChangeAccountGroupController.cs › ChangeAccountGroupController.ChangeGroup` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `ChangeAccountGroupController.ChangeGroup`
2. Action body in `TZTigoMChangoService/Controllers/MobileControllers/ChangeAccountGroupController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as ChangeAccountGroupController
  participant Svc as downstream
  App->>Ctrl: GET /api/web/ChangeAccountGroup/ChangeGroup
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
| See service data-model | R/W | Traced at SHA 7c288ab |

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
| — | 400 | — | reachable return | transactionStatus = "No valid account IDs provided. Use comma-separated ids, e.g. ?ids=1,2,3", success = false  | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/mchango/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-MChango/TZTigoMChangoService/Controllers/MobileControllers/ChangeAccountGroupController.cs › ChangeAccountGroupController.ChangeGroup` @ `7c288ab`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
