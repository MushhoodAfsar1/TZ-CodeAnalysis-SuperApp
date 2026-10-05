---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-335]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-335 MixxTipInternalController.GetStaffMsisdn
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/Internal/MixxTipInternalController.cs › MixxTipInternalController.GetStaffMsisdn` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/internal/mixxtip/staff/getmsisdn
  internal_path: /api/internal/mixxtip/staff/getmsisdn
  dispatch_field: null
  dispatch_value: null
  controller_action: MixxTipInternalController.GetStaffMsisdn
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| staffcode | `string?` | no | — | DataAnnotations / action | — |
| staffmsisdn | `string?` | no | — | DataAnnotations / action | — |
| staffmsisdn | `string` | no | — | DataAnnotations / action | — |
| mixxtipamount | `decimal` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "staffcode": "<staffcode>", "staffmsisdn": "<staffmsisdn>", "staffmsisdn": "<staffmsisdn>", "mixxtipamount": "<mixxtipamount>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Guard: success = false, responseMessage_en = "staffcode or staffmsisdn is required.", responseMessage_fr = "staffcode ou staffmsisdn est requis."  | HTTP 400 | — | `TZTigoSuperAppConfiguration/Controllers/Internal/MixxTipInternalController.cs › MixxTipInternalController.GetStaffMsisdn` |
| 2 | Guard: staffcode or staffmsisdn is required. | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/Internal/MixxTipInternalController.cs › MixxTipInternalController.GetStaffMsisdn` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `MixxTipInternalController.GetStaffMsisdn`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/Internal/MixxTipInternalController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as MixxTipInternalController
  participant Svc as downstream
  App->>Ctrl: POST /api/internal/mixxtip/staff/getmsisdn
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
| — | 400 | — | reachable return | success = false, responseMessage_en = "staffcode or staffmsisdn is required.", responseMessage_fr = "staffcode ou staffmsisdn est requis."  | no |
| — | 200-envelope | — | success=false envelope | staffcode or staffmsisdn is required. | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/config/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/Internal/MixxTipInternalController.cs › MixxTipInternalController.GetStaffMsisdn` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
