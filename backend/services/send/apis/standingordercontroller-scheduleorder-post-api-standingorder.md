---
kb_section: backend
type: api-contract
ids: [BE-API-SEND-007]
service: SEND
repo: TZ-Tigo-SuperApp-SendMoney
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 599771b
updated: 2026-10-05
confidence: confirmed
---
# BE-API-SEND-007 StandingOrderController.ScheduleOrder
**Service:** BE-SVC-SEND · **Handler:** `TZ-Tigo-SuperApp-SendMoney/TZTigoSuperAppSendMoney/Controllers/StandingOrderController.cs › StandingOrderController.ScheduleOrder` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/StandingOrder
  internal_path: /api/StandingOrder
  dispatch_field: null
  dispatch_value: null
  controller_action: StandingOrderController.ScheduleOrder
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** ScheduleOrderRequestDTO

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| CustomerId | `string?` | no | — | DataAnnotations / action | — |
| Msisdn | `string?` | no | — | DataAnnotations / action | — |
| FullName | `string?` | no | — | DataAnnotations / action | — |
| Source | `string?` | no | — | DataAnnotations / action | — |
| OrderName | `string?` | no | — | DataAnnotations / action | — |
| Duration | `string?` | no | — | DataAnnotations / action | — |
| StartDate | `DateTime?` | no | — | DataAnnotations / action | — |
| EndDate | `DateTime?` | no | — | DataAnnotations / action | — |
| NextPayment | `DateTime?` | no | — | DataAnnotations / action | — |
| LastPayment | `DateTime?` | no | — | DataAnnotations / action | — |
| OrderReference | `string?` | no | — | DataAnnotations / action | — |
| OrderReferenceName | `string?` | no | — | DataAnnotations / action | — |
| Destination | `string?` | no | — | DataAnnotations / action | — |
| Mno | `string?` | no | — | DataAnnotations / action | — |
| Brand | `string?` | no | — | DataAnnotations / action | — |
| ShortCode | `string?` | no | — | DataAnnotations / action | — |
| Status | `string?` | no | — | DataAnnotations / action | — |
| Type | `string?` | no | — | DataAnnotations / action | — |
| RequestChannel | `string?` | no | — | DataAnnotations / action | — |
| Amount | `decimal?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "CustomerId": "<CustomerId>", "Msisdn": "<Msisdn>", "FullName": "<FullName>", "Source": "<Source>", "OrderName": "<OrderName>", "Duration": "<Duration>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `StandingOrderController.ScheduleOrder`
2. Action body in `TZTigoSuperAppSendMoney/Controllers/StandingOrderController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as StandingOrderController
  participant Svc as downstream
  App->>Ctrl: POST /api/StandingOrder
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
- `TZ-Tigo-SuperApp-SendMoney/TZTigoSuperAppSendMoney/Controllers/StandingOrderController.cs › StandingOrderController.ScheduleOrder` @ `599771b`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
