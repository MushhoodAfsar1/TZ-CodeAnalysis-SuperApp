---
kb_section: backend
type: api-contract
ids: [BE-API-AIRTIME-002]
service: AIRTIME
repo: TZ-Tigo-SuperApp-AirTimeTopup
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 7a52359
updated: 2026-10-05
confidence: confirmed
---
# BE-API-AIRTIME-002 FiberProductController.SubmitPayment
**Service:** BE-SVC-AIRTIME · **Handler:** `TZ-Tigo-SuperApp-AirTimeTopup/TZTigoSuperAppAirTimeTopup/Controllers/FiberProductController.cs › FiberProductController.SubmitPayment` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/FiberProduct
  internal_path: /api/FiberProduct
  dispatch_field: null
  dispatch_value: null
  controller_action: FiberProductController.SubmitPayment
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** SubmitPaymentRequest

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| UserName | `string` | yes | — | DataAnnotations / action | — |
| Password | `string` | yes | — | DataAnnotations / action | — |
| Msisdn | `string` | yes | — | DataAnnotations / action | — |
| Amount | `string` | yes | — | DataAnnotations / action | — |
| ReferenceNumber | `string` | yes | — | DataAnnotations / action | — |
| ProductCode | `string` | yes | — | DataAnnotations / action | — |
| Duration | `string?` | no | — | DataAnnotations / action | — |
| isCapacityChange | `bool` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "UserName": "<UserName>", "Password": "<Password>", "Msisdn": "<Msisdn>", "Amount": "<Amount>", "ReferenceNumber": "<ReferenceNumber>", "ProductCode": "<ProductCode>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `FiberProductController.SubmitPayment`
2. Action body in `TZTigoSuperAppAirTimeTopup/Controllers/FiberProductController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as FiberProductController
  participant Svc as downstream
  App->>Ctrl: POST /api/FiberProduct
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
| See service data-model | R/W | Traced at SHA 7a52359 |

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
See `services/airtime/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-AirTimeTopup/TZTigoSuperAppAirTimeTopup/Controllers/FiberProductController.cs › FiberProductController.SubmitPayment` @ `7a52359`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
