---
kb_section: backend
type: api-contract
ids: [BE-API-MCHANGO-008]
service: MCHANGO
repo: TZ-Tigo-SuperApp-MChango
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 7c288ab
updated: 2026-10-05
confidence: confirmed
---
# BE-API-MCHANGO-008 NotificationController.SendMchangoNotfication
**Service:** BE-SVC-MCHANGO · **Handler:** `TZ-Tigo-SuperApp-MChango/TZTigoMChangoService/Controllers/MobileControllers/NotificationController.cs › NotificationController.SendMchangoNotfication` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/mobile/Notification/SendMchangoNotfication
  internal_path: /api/mobile/Notification/SendMchangoNotfication
  dispatch_field: null
  dispatch_value: null
  controller_action: NotificationController.SendMchangoNotfication
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| requestingOrganisationTransactionReference | `string?` | no | — | DataAnnotations / action | — |
| useCaseName | `string?` | no | — | DataAnnotations / action | — |
| isMerchant | `bool?` | no | — | DataAnnotations / action | — |
| pushUpdateStatus | `bool` | no | — | DataAnnotations / action | — |
| ipInfo | `string?` | no | — | DataAnnotations / action | — |
| channel | `string?` | no | — | DataAnnotations / action | — |
| appVersion | `string?` | no | — | DataAnnotations / action | — |
| languageCode | `string?` | no | — | DataAnnotations / action | — |
| deviceId | `string?` | no | — | DataAnnotations / action | — |
| deviceMaker | `string?` | no | — | DataAnnotations / action | — |
| deviceType | `string?` | no | — | DataAnnotations / action | — |
| OS | `string?` | no | — | DataAnnotations / action | — |
| pushId | `string?` | no | — | DataAnnotations / action | — |
| latitude | `string?` | no | — | DataAnnotations / action | — |
| longitude | `string?` | no | — | DataAnnotations / action | — |
| transactionId | `string?` | no | — | DataAnnotations / action | — |
| sourceMsisdn | `string?` | no | — | DataAnnotations / action | — |
| receiverMsisdn | `string?` | no | — | DataAnnotations / action | — |
| receiverAccountNo | `string?` | no | — | DataAnnotations / action | — |
| senderName | `string?` | no | — | DataAnnotations / action | — |
| amount | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "requestingOrganisationTransactionReference": "<requestingOrganisationTransactionReference>", "useCaseName": "<useCaseName>", "isMerchant": "<isMerchant>", "pushUpdateStatus": "<pushUpdateStatus>", "ipInfo": "<ipInfo>", "channel": "<channel>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `NotificationController.SendMchangoNotfication`
2. Action body in `TZTigoMChangoService/Controllers/MobileControllers/NotificationController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as NotificationController
  participant Svc as downstream
  App->>Ctrl: POST /api/mobile/Notification/SendMchangoNotfication
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
- `TZ-Tigo-SuperApp-MChango/TZTigoMChangoService/Controllers/MobileControllers/NotificationController.cs › NotificationController.SendMchangoNotfication` @ `7c288ab`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
