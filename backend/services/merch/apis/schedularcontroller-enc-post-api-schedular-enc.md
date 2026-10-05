---
kb_section: backend
type: api-contract
ids: [BE-API-MERCH-043]
service: MERCH
repo: TZ-Tigo-SuperApp-Merchant
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 2367767
updated: 2026-10-05
confidence: confirmed
---
# BE-API-MERCH-043 SchedularController.enc
**Service:** BE-SVC-MERCH · **Handler:** `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/SchedularController.cs › SchedularController.enc` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Schedular/enc
  internal_path: /api/Schedular/enc
  dispatch_field: null
  dispatch_value: null
  controller_action: SchedularController.enc
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| Id | `int` | no | — | DataAnnotations / action | — |
| Scheduler_Id | `int?` | no | — | DataAnnotations / action | — |
| PIN | `string?` | no | — | DataAnnotations / action | — |
| MSISDN | `string?` | no; max 50 | — | DataAnnotations / action | — |
| ReceiverMSISDN | `string?` | no; max 50 | — | DataAnnotations / action | — |
| AccountType | `string?` | no | — | DataAnnotations / action | — |
| PaymentOption | `PaymentOption?` | no | — | DataAnnotations / action | — |
| Amount | `string?` | no | — | DataAnnotations / action | — |
| BankId | `string?` | no; max 50 | — | DataAnnotations / action | — |
| shortCode | `string?` | no | — | DataAnnotations / action | — |
| targetRefNumber | `string?` | no | — | DataAnnotations / action | — |
| PaymentType | `string?` | no | — | DataAnnotations / action | — |
| ChannelUser | `string?` | no | — | DataAnnotations / action | — |
| ChannelPass | `string?` | no | — | DataAnnotations / action | — |
| PaymentPercentage | `string?` | no | — | DataAnnotations / action | — |
| ScheduleType | `ScheduleType` | yes | — | DataAnnotations / action | — |
| ScheduleValue | `float` | yes | — | DataAnnotations / action | — |
| IsActive | `bool?` | no | — | DataAnnotations / action | — |
| NextExecutionTime | `DateTime?` | no | — | DataAnnotations / action | — |
| ScheduleTime | `string?` | no | — | DataAnnotations / action | — |
| IsUtilized | `bool` | no | — | DataAnnotations / action | — |
| ThreadID | `string?` | no | — | DataAnnotations / action | — |
| UtilizationDateTime | `DateTime?` | no | — | DataAnnotations / action | — |
| CreatedBy | `string?` | yes | — | DataAnnotations / action | — |
| CreatedDate | `DateTime` | yes | — | DataAnnotations / action | — |
| ModifiedBy | `string?` | no | — | DataAnnotations / action | — |
| ModifiedDate | `DateTime?` | no | — | DataAnnotations / action | — |
| IsDeleted | `bool` | no | — | DataAnnotations / action | — |
| requestingOrganisationTransactionReference | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "Id": "<Id>", "Scheduler_Id": "<Scheduler_Id>", "PIN": "<PIN>", "MSISDN": "<MSISDN>", "ReceiverMSISDN": "<ReceiverMSISDN>", "AccountType": "<AccountType>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `SchedularController.enc`
2. Action body in `TZTigoSuperAppMerchant/Controllers/SchedularController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as SchedularController
  participant Svc as downstream
  App->>Ctrl: POST /api/Schedular/enc
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
- `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/SchedularController.cs › SchedularController.enc` @ `2367767`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
