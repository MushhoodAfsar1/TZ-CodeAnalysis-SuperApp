---
kb_section: backend
type: api-contract
ids: [BE-API-MCHANGO-041]
service: MCHANGO
repo: TZ-Tigo-SuperApp-MChango
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 7c288ab
updated: 2026-10-05
confidence: confirmed
---
# BE-API-MCHANGO-041 RTTController.CreateRTT
**Service:** BE-SVC-MCHANGO · **Handler:** `TZ-Tigo-SuperApp-MChango/TZTigoMChangoService/Controllers/MobileControllers/RTTController.cs › RTTController.CreateRTT` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/mobile/RTT/CreateRTT
  internal_path: /api/mobile/RTT/CreateRTT
  dispatch_field: null
  dispatch_value: null
  controller_action: RTTController.CreateRTT
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| BrandGroupName | `string?` | no | — | DataAnnotations / action | — |
| BrandID | `string?` | no | — | DataAnnotations / action | — |
| BrandName | `string?` | no | — | DataAnnotations / action | — |
| CreditAmount | `decimal?` | no | — | DataAnnotations / action | — |
| DebitAmount | `decimal?` | no | — | DataAnnotations / action | — |
| DestCustomerMobile | `string?` | no | — | DataAnnotations / action | — |
| DestCustomerFullName | `string?` | no | — | DataAnnotations / action | — |
| DestCustomerGroupName | `string?` | no | — | DataAnnotations / action | — |
| DestFees1 | `decimal?` | no | — | DataAnnotations / action | — |
| DestFees2 | `decimal?` | no | — | DataAnnotations / action | — |
| DestFees3 | `decimal?` | no | — | DataAnnotations / action | — |
| DestFees4 | `decimal?` | no | — | DataAnnotations / action | — |
| DestLevy | `decimal?` | no | — | DataAnnotations / action | — |
| DestTaxOnLevy | `decimal?` | no | — | DataAnnotations / action | — |
| ExternalMemo | `string?` | no | — | DataAnnotations / action | — |
| OriginalAmount | `decimal` | no | — | DataAnnotations / action | — |
| PayableAmount | `decimal?` | no | — | DataAnnotations / action | — |
| SalesOrderStatus | `string` | no | — | DataAnnotations / action | — |
| SalesOrderNumber | `string` | no | — | DataAnnotations / action | — |
| ServiceName | `string` | no | — | DataAnnotations / action | — |
| SourceCustomerMobile | `string?` | no | — | DataAnnotations / action | — |
| SenderAccountNumber | `string?` | no | — | DataAnnotations / action | — |
| SourceCustomerAlias | `string?` | no | — | DataAnnotations / action | — |
| SourceCustomerFullName | `string?` | no | — | DataAnnotations / action | — |
| SourceCustomerGroupName | `string?` | no | — | DataAnnotations / action | — |
| SourceCustomerId | `string?` | no | — | DataAnnotations / action | — |
| SourceFees1 | `decimal?` | no | — | DataAnnotations / action | — |
| SourceFees2 | `decimal?` | no | — | DataAnnotations / action | — |
| SourceFees3 | `decimal?` | no | — | DataAnnotations / action | — |
| SourceFees4 | `decimal?` | no | — | DataAnnotations / action | — |
| SrcLevy | `decimal?` | no | — | DataAnnotations / action | — |
| SrcTaxOnLevy | `decimal?` | no | — | DataAnnotations / action | — |
| TransactionDate | `long?` | no | — | DataAnnotations / action | — |
| ExtReferenceId | `string?` | no | — | DataAnnotations / action | — |
| ExtraInfo1 | `string?` | no | — | DataAnnotations / action | — |
| ExternalReference | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "BrandGroupName": "<BrandGroupName>", "BrandID": "<BrandID>", "BrandName": "<BrandName>", "CreditAmount": "<CreditAmount>", "DebitAmount": "<DebitAmount>", "DestCustomerMobile": "<DestCustomerMobile>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `RTTController.CreateRTT`
2. Action body in `TZTigoMChangoService/Controllers/MobileControllers/RTTController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as RTTController
  participant Svc as downstream
  App->>Ctrl: POST /api/mobile/RTT/CreateRTT
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
| See service data-model | R/W | Traced at SHA 7c288ab |

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
See `services/mchango/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-MChango/TZTigoMChangoService/Controllers/MobileControllers/RTTController.cs › RTTController.CreateRTT` @ `7c288ab`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
