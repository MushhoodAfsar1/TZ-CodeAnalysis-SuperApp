---
kb_section: backend
type: api-contract
ids: [BE-API-MERCH-042]
service: MERCH
repo: TZ-Tigo-SuperApp-Merchant
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 2367767
updated: 2026-10-05
confidence: confirmed
---
# BE-API-MERCH-042 SchedularController.MerchantLinkAccount
**Service:** BE-SVC-MERCH · **Handler:** `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/SchedularController.cs › SchedularController.MerchantLinkAccount` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Schedular/MerchantLinkAccount
  internal_path: /api/Schedular/MerchantLinkAccount
  dispatch_field: null
  dispatch_value: null
  controller_action: SchedularController.MerchantLinkAccount
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** MerchantLinkAccountRequest

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| OperationType | `string?` | no | — | DataAnnotations / action | — |
| SenderMsisdn | `string?` | no | — | DataAnnotations / action | — |
| RecieverMsisdn | `string?` | no | — | DataAnnotations / action | — |
| PINCode | `string?` | no | — | DataAnnotations / action | — |
| SessionToken | `string?` | no | — | DataAnnotations / action | — |
| ReferenceName | `string?` | no | — | DataAnnotations / action | — |
| PaymentType | `PaymentType?` | no | — | DataAnnotations / action | — |
| Amount | `string?` | no | — | DataAnnotations / action | — |
| ReferenceNo | `string?` | no | — | DataAnnotations / action | — |
| BankId | `string?` | no | — | DataAnnotations / action | — |
| scheduleId | `long?` | no | — | DataAnnotations / action | — |
| recId | `long?` | no | — | DataAnnotations / action | — |
| Msisdn | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "OperationType": "<OperationType>", "SenderMsisdn": "<SenderMsisdn>", "RecieverMsisdn": "<RecieverMsisdn>", "PINCode": "<PINCode>", "SessionToken": "<SessionToken>", "ReferenceName": "<ReferenceName>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `SchedularController.MerchantLinkAccount`
2. Action body in `TZTigoSuperAppMerchant/Controllers/SchedularController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as SchedularController
  participant Svc as downstream
  App->>Ctrl: POST /api/Schedular/MerchantLinkAccount
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
- `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/SchedularController.cs › SchedularController.MerchantLinkAccount` @ `2367767`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
