---
kb_section: backend
type: api-contract
ids: [BE-API-SELFC-038]
service: SELFC
repo: TZ-Tigo-SuperApp-SelfCare
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: a0aeca8
updated: 2026-10-05
confidence: confirmed
---
# BE-API-SELFC-038 UnsolicitedSMSController.SaveSMS
**Service:** BE-SVC-SELFC · **Handler:** `TZ-Tigo-SuperApp-SelfCare/TZTigoSuperAppSelfcare/Controllers/UnsolicitedSMSController.cs › UnsolicitedSMSController.SaveSMS` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api
  internal_path: /api
  dispatch_field: null
  dispatch_value: null
  controller_action: UnsolicitedSMSController.SaveSMS
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** SaveSMSRequestDTO

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| operation | `string` | no | — | DataAnnotations / action | — |
| msisdn | `string` | no | — | DataAnnotations / action | — |
| data | `RequestPayloadDto?` | no | — | DataAnnotations / action | — |
| categoryid | `List<int>?` | no | — | DataAnnotations / action | — |
| senderid | `List<string>?` | no | — | DataAnnotations / action | — |
| msisdn | `string?` | no | — | DataAnnotations / action | — |
| smsReadingModel | `List<SMSMessage>` | no | — | DataAnnotations / action | — |
| id | `string?` | no | — | DataAnnotations / action | — |
| from | `string?` | no | — | DataAnnotations / action | — |
| timestamp | `string?` | no | — | DataAnnotations / action | — |
| body | `string?` | no | — | DataAnnotations / action | — |
| serviceCenterAddress | `string?` | no | — | DataAnnotations / action | — |
| Msisdn | `string` | no | — | DataAnnotations / action | — |
| isShowPrompt | `bool?` | no | — | DataAnnotations / action | — |
| UserPreference | `bool?` | no | — | DataAnnotations / action | — |
| Message | `string` | no | — | DataAnnotations / action | — |
| NextPromptDate | `DateTime?` | no | — | DataAnnotations / action | — |
| Msisdn | `string` | no | — | DataAnnotations / action | — |
| OptIn | `bool` | no | — | DataAnnotations / action | — |
| IsOptedIn | `bool` | no | — | DataAnnotations / action | — |
| Message | `string` | no | — | DataAnnotations / action | — |
| NextPromptDate | `DateTime?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "operation": "<operation>", "msisdn": "<msisdn>", "data": "<data>", "categoryid": "<categoryid>", "senderid": "<senderid>", "msisdn": "<msisdn>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `UnsolicitedSMSController.SaveSMS`
2. Action body in `TZTigoSuperAppSelfcare/Controllers/UnsolicitedSMSController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as UnsolicitedSMSController
  participant Svc as downstream
  App->>Ctrl: POST /api
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
| See service data-model | R/W | Traced at SHA a0aeca8 |

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
See `services/selfc/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-SelfCare/TZTigoSuperAppSelfcare/Controllers/UnsolicitedSMSController.cs › UnsolicitedSMSController.SaveSMS` @ `a0aeca8`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
