---
kb_section: backend
type: api-contract
ids: [BE-API-EXTPAY-001]
service: EXTPAY
repo: TZ-Tigo-SuperApp-ExternalPayment
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 51718e1
updated: 2026-10-05
confidence: confirmed
---
# BE-API-EXTPAY-001 ExternalPaymentController.ValidateBillerDetails
**Service:** BE-SVC-EXTPAY · **Handler:** `TZ-Tigo-SuperApp-ExternalPayment/TZTigoSuperAppExternalPayment/Controllers/ExternalPaymentController.cs › ExternalPaymentController.ValidateBillerDetails` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/ExternalPayment
  internal_path: /api/ExternalPayment
  dispatch_field: null
  dispatch_value: null
  controller_action: ExternalPaymentController.ValidateBillerDetails
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** ValidateBillerDetailsRequest

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| consumerID | `string?` | no | — | DataAnnotations / action | — |
| referenceID | `string?` | no | — | DataAnnotations / action | — |
| sourceMSISDN | `string?` | no | — | DataAnnotations / action | — |
| sourcePIN | `string?` | no | — | DataAnnotations / action | — |
| terminalType | `string?` | no | — | DataAnnotations / action | — |
| targetRefNumber | `string?` | no | — | DataAnnotations / action | — |
| amount | `string?` | no | — | DataAnnotations / action | — |
| shortCode | `string?` | no | — | DataAnnotations / action | — |
| IsBankTransfer | `bool` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "consumerID": "<consumerID>", "referenceID": "<referenceID>", "sourceMSISDN": "<sourceMSISDN>", "sourcePIN": "<sourcePIN>", "terminalType": "<terminalType>", "targetRefNumber": "<targetRefNumber>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `ExternalPaymentController.ValidateBillerDetails`
2. Action body in `TZTigoSuperAppExternalPayment/Controllers/ExternalPaymentController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as ExternalPaymentController
  participant Svc as downstream
  App->>Ctrl: POST /api/ExternalPayment
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
| See service data-model | R/W | Traced at SHA 51718e1 |

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
See `services/extpay/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-ExternalPayment/TZTigoSuperAppExternalPayment/Controllers/ExternalPaymentController.cs › ExternalPaymentController.ValidateBillerDetails` @ `51718e1`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
