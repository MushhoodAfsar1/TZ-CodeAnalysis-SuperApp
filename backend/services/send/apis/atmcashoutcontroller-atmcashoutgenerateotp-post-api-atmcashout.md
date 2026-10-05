---
kb_section: backend
type: api-contract
ids: [BE-API-SEND-015]
service: SEND
repo: TZ-Tigo-SuperApp-SendMoney
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 599771b
updated: 2026-10-05
confidence: confirmed
---
# BE-API-SEND-015 ATMCashoutController.ATMCashoutGenerateOtp
**Service:** BE-SVC-SEND · **Handler:** `TZ-Tigo-SuperApp-SendMoney/TZTigoSuperAppSendMoney/Controllers/ATMCashoutController.cs › ATMCashoutController.ATMCashoutGenerateOtp` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/ATMCashout
  internal_path: /api/ATMCashout
  dispatch_field: null
  dispatch_value: null
  controller_action: ATMCashoutController.ATMCashoutGenerateOtp
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** ATMCashoutGenerateOtpRequest

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| AtmId | `string?` | no | — | DataAnnotations / action | — |
| CustomerMSISDN | `string?` | no | — | DataAnnotations / action | — |
| Amount | `string?` | no | — | DataAnnotations / action | — |
| PIN | `string?` | no | — | DataAnnotations / action | — |
| ATMID | `int?` | no | — | DataAnnotations / action | — |
| CustomerMSISDN | `string?` | no | — | DataAnnotations / action | — |
| Amount | `int?` | no | — | DataAnnotations / action | — |
| PIN | `string?` | no | — | DataAnnotations / action | — |
| ReferenceID | `string?` | no | — | DataAnnotations / action | — |
| SessionID | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "AtmId": "<AtmId>", "CustomerMSISDN": "<CustomerMSISDN>", "Amount": "<Amount>", "PIN": "<PIN>", "ATMID": "<ATMID>", "CustomerMSISDN": "<CustomerMSISDN>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `ATMCashoutController.ATMCashoutGenerateOtp`
2. Action body in `TZTigoSuperAppSendMoney/Controllers/ATMCashoutController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as ATMCashoutController
  participant Svc as downstream
  App->>Ctrl: POST /api/ATMCashout
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
| See service data-model | R/W | Traced at SHA 599771b |

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
See `services/send/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-SendMoney/TZTigoSuperAppSendMoney/Controllers/ATMCashoutController.cs › ATMCashoutController.ATMCashoutGenerateOtp` @ `599771b`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
