---
kb_section: backend
type: api-contract
ids: [BE-API-SEND-006]
service: SEND
repo: TZ-Tigo-SuperApp-SendMoney
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 599771b
updated: 2026-10-05
confidence: confirmed
---
# BE-API-SEND-006 SendMoneyController.encTransfer
**Service:** BE-SVC-SEND · **Handler:** `TZ-Tigo-SuperApp-SendMoney/TZTigoSuperAppSendMoney/Controllers/SendMoneyController.cs › SendMoneyController.encTransfer` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/SendMoney/encTransfer
  internal_path: /api/SendMoney/encTransfer
  dispatch_field: null
  dispatch_value: null
  controller_action: SendMoneyController.encTransfer
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| transferMoney | `List<TransferMoney>?` | no | — | DataAnnotations / action | — |
| customData | `List<customData>?` | no | — | DataAnnotations / action | — |
| isMerchant | `bool?` | no | — | DataAnnotations / action | — |
| transactionType | `string?` | no | — | DataAnnotations / action | — |
| consumerID | `string?` | no | — | DataAnnotations / action | — |
| referenceID | `string?` | no | — | DataAnnotations / action | — |
| sourceMSISDN | `string?` | no | — | DataAnnotations / action | — |
| sourcePIN | `string?` | no | — | DataAnnotations / action | — |
| terminalType | `string?` | no | — | DataAnnotations / action | — |
| targetMSISDN | `string?` | no | — | DataAnnotations / action | — |
| amount | `string?` | no | — | DataAnnotations / action | — |
| shortCode | `string?` | no | — | DataAnnotations / action | — |
| inclCOFee | `bool?` | no | — | DataAnnotations / action | — |
| overdraftBrandID | `string?` | no | — | DataAnnotations / action | — |
| channelPass | `string?` | no | — | DataAnnotations / action | — |
| channelUser | `string?` | no | — | DataAnnotations / action | — |
| paymentType | `string?` | no | — | DataAnnotations / action | — |
| storeLabel | `string?` | no | — | DataAnnotations / action | — |
| isTip | `bool` | no | — | DataAnnotations / action | — |
| key | `string?` | no | — | DataAnnotations / action | — |
| value | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "transferMoney": "<transferMoney>", "customData": "<customData>", "isMerchant": "<isMerchant>", "transactionType": "<transactionType>", "consumerID": "<consumerID>", "referenceID": "<referenceID>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `SendMoneyController.encTransfer`
2. Action body in `TZTigoSuperAppSendMoney/Controllers/SendMoneyController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as SendMoneyController
  participant Svc as downstream
  App->>Ctrl: POST /api/SendMoney/encTransfer
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
- `TZ-Tigo-SuperApp-SendMoney/TZTigoSuperAppSendMoney/Controllers/SendMoneyController.cs › SendMoneyController.encTransfer` @ `599771b`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
