---
kb_section: backend
type: api-contract
ids: [BE-API-INSUR-007]
service: INSUR
repo: TZ-Tigo-SuperApp-Insurrance
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 38747da
updated: 2026-10-05
confidence: confirmed
---
# BE-API-INSUR-007 InsuranceController.GetVehicleDetails
**Service:** BE-SVC-INSUR · **Handler:** `TZ-Tigo-SuperApp-Insurrance/TZTigoSuperAppInsurance/Controllers/InsuranceController.cs › InsuranceController.GetVehicleDetails` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Insurance
  internal_path: /api/Insurance
  dispatch_field: null
  dispatch_value: null
  controller_action: InsuranceController.GetVehicleDetails
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** GetVehicleDetailsRequest

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| (none / untyped) | — | — | — | — | See evidence |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "note": "<none>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `InsuranceController.GetVehicleDetails`
2. Action body in `TZTigoSuperAppInsurance/Controllers/InsuranceController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as InsuranceController
  participant Svc as downstream
  App->>Ctrl: POST /api/Insurance
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
| See service data-model | R/W | Traced at SHA 38747da |

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
See `services/insur/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Insurrance/TZTigoSuperAppInsurance/Controllers/InsuranceController.cs › InsuranceController.GetVehicleDetails` @ `38747da`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
