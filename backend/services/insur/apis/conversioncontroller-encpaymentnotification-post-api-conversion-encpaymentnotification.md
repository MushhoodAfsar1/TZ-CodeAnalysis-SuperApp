---
kb_section: backend
type: api-contract
ids: [BE-API-INSUR-006]
service: INSUR
repo: TZ-Tigo-SuperApp-Insurrance
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 38747da
updated: 2026-10-05
confidence: confirmed
---
# BE-API-INSUR-006 ConversionController.encPaymentNotification
**Service:** BE-SVC-INSUR · **Handler:** `TZ-Tigo-SuperApp-Insurrance/TZTigoSuperAppInsurance/Controllers/ConversionController.cs › ConversionController.encPaymentNotification` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Conversion/encPaymentNotification
  internal_path: /api/Conversion/encPaymentNotification
  dispatch_field: null
  dispatch_value: null
  controller_action: ConversionController.encPaymentNotification
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| transactionRef | `string?` | no | — | DataAnnotations / action | — |
| transactionChannel | `string?` | no | — | DataAnnotations / action | — |
| transactionDate | `string?` | no | — | DataAnnotations / action | — |
| payerName | `string?` | no | — | DataAnnotations / action | — |
| payerID | `string?` | no | — | DataAnnotations / action | — |
| paymentReference | `string?` | no | — | DataAnnotations / action | — |
| amount | `string?` | no | — | DataAnnotations / action | — |
| currency | `string?` | no | — | DataAnnotations / action | — |
| amountType | `string?` | no | — | DataAnnotations / action | — |
| paymentDesc | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "transactionRef": "<transactionRef>", "transactionChannel": "<transactionChannel>", "transactionDate": "<transactionDate>", "payerName": "<payerName>", "payerID": "<payerID>", "paymentReference": "<paymentReference>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `ConversionController.encPaymentNotification`
2. Action body in `TZTigoSuperAppInsurance/Controllers/ConversionController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as ConversionController
  participant Svc as downstream
  App->>Ctrl: POST /api/Conversion/encPaymentNotification
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
- `TZ-Tigo-SuperApp-Insurrance/TZTigoSuperAppInsurance/Controllers/ConversionController.cs › ConversionController.encPaymentNotification` @ `38747da`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
