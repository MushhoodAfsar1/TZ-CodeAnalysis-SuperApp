---
kb_section: backend
type: api-contract
ids: [BE-API-DSTV-007]
service: DSTV
repo: TZ-Tigo-SuperApp-DigitalSubscription
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: fd31aa1
updated: 2026-10-05
confidence: confirmed
---
# BE-API-DSTV-007 DSTVController.DueAmountenc
**Service:** BE-SVC-DSTV · **Handler:** `TZ-Tigo-SuperApp-DigitalSubscription/TZTigoSuperAppDigitalSubscription/Controllers/DSTVController.cs › DSTVController.DueAmountenc` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/DSTV/DueAmountenc
  internal_path: /api/DSTV/DueAmountenc
  dispatch_field: null
  dispatch_value: null
  controller_action: DSTVController.DueAmountenc
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| dataSource | `string` | no | — | DataAnnotations / action | — |
| scNumber | `string` | no | — | DataAnnotations / action | — |
| vendorCode | `string` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "dataSource": "<dataSource>", "scNumber": "<scNumber>", "vendorCode": "<vendorCode>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `DSTVController.DueAmountenc`
2. Action body in `TZTigoSuperAppDigitalSubscription/Controllers/DSTVController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as DSTVController
  participant Svc as downstream
  App->>Ctrl: POST /api/DSTV/DueAmountenc
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
| See service data-model | R/W | Traced at SHA fd31aa1 |

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
See `services/dstv/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-DigitalSubscription/TZTigoSuperAppDigitalSubscription/Controllers/DSTVController.cs › DSTVController.DueAmountenc` @ `fd31aa1`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
