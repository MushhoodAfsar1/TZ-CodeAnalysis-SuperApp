---
kb_section: backend
type: api-contract
ids: [BE-API-WALLET-001]
service: WALLET
repo: TZ-Tigo-SuperApp-Wallet
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 27737b1
updated: 2026-10-05
confidence: confirmed
---
# BE-API-WALLET-001 CashOutController.CashOutFee
**Service:** BE-SVC-WALLET · **Handler:** `TZ-Tigo-SuperApp-Wallet/TZTigoSuperAppWallet/Controllers/CashOutController.cs › CashOutController.CashOutFee` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/CashOut/cashOutFee
  internal_path: /api/CashOut/cashOutFee
  dispatch_field: null
  dispatch_value: null
  controller_action: CashOutController.CashOutFee
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** CashOutFeeRequestDto

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| consumerID | `string` | no | — | DataAnnotations / action | — |
| country | `string` | no | — | DataAnnotations / action | — |
| correlationID | `string` | no | — | DataAnnotations / action | — |
| msisdn | `string` | no | — | DataAnnotations / action | — |
| creditParty | `creditParty` | no | — | DataAnnotations / action | — |
| amount | `string` | no | — | DataAnnotations / action | — |
| transactionType | `string` | no | — | DataAnnotations / action | — |
| shortCode | `string` | no | — | DataAnnotations / action | — |
| key | `string` | no | — | DataAnnotations / action | — |
| value | `string` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "consumerID": "<consumerID>", "country": "<country>", "correlationID": "<correlationID>", "msisdn": "<msisdn>", "creditParty": "<creditParty>", "amount": "<amount>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `CashOutController.CashOutFee`
2. Action body in `TZTigoSuperAppWallet/Controllers/CashOutController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as CashOutController
  participant Svc as downstream
  App->>Ctrl: POST /api/CashOut/cashOutFee
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
| See service data-model | R/W | Traced at SHA 27737b1 |

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
See `services/wallet/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Wallet/TZTigoSuperAppWallet/Controllers/CashOutController.cs › CashOutController.CashOutFee` @ `27737b1`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
