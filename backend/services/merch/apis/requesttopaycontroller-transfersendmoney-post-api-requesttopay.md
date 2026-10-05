---
kb_section: backend
type: api-contract
ids: [BE-API-MERCH-034]
service: MERCH
repo: TZ-Tigo-SuperApp-Merchant
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 2367767
updated: 2026-10-05
confidence: confirmed
---
# BE-API-MERCH-034 RequestToPayController.TransferSendMoney
**Service:** BE-SVC-MERCH · **Handler:** `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs › RequestToPayController.TransferSendMoney` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/RequestToPay
  internal_path: /api/RequestToPay
  dispatch_field: null
  dispatch_value: null
  controller_action: RequestToPayController.TransferSendMoney
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** TransferSendMoneyRequest

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| isMerchant | `bool?` | no | — | DataAnnotations / action | — |
| transferMoney | `List<TransferMoney>?` | no | — | DataAnnotations / action | — |
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

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "isMerchant": "<isMerchant>", "transferMoney": "<transferMoney>", "consumerID": "<consumerID>", "referenceID": "<referenceID>", "sourceMSISDN": "<sourceMSISDN>", "sourcePIN": "<sourcePIN>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `RequestToPayController.TransferSendMoney`
2. Action body in `TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as RequestToPayController
  participant Svc as downstream
  App->>Ctrl: POST /api/RequestToPay
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
| See service data-model | R/W | Traced at SHA 2367767 |

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
See `services/merch/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs › RequestToPayController.TransferSendMoney` @ `2367767`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
