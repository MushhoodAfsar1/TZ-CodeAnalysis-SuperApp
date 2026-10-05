---
kb_section: backend
type: api-contract
ids: [BE-API-NOTIF-016]
service: NOTIF
repo: TZ-Tigo-SuperApp-Notification
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: b7c98ec
updated: 2026-10-05
confidence: confirmed
---
# BE-API-NOTIF-016 NotificationTemplateController.DeleteNotificationTemplate
**Service:** BE-SVC-NOTIF · **Handler:** `TZ-Tigo-SuperApp-Notification/TZTigoSuperAppNotification/Controllers/NotificationTemplateController.cs › NotificationTemplateController.DeleteNotificationTemplate` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/NotificationTemplate/delete
  internal_path: /api/NotificationTemplate/delete
  dispatch_field: null
  dispatch_value: null
  controller_action: NotificationTemplateController.DeleteNotificationTemplate
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| Id | `int?` | no | — | DataAnnotations / action | — |
| createdBy | `string?` | no | — | DataAnnotations / action | — |
| createdDate | `DateTime?` | no | — | DataAnnotations / action | — |
| updatedBy | `string?` | no | — | DataAnnotations / action | — |
| updatedDate | `DateTime?` | no | — | DataAnnotations / action | — |
| languageCode | `string?` | no | — | DataAnnotations / action | — |
| flowId | `string?` | no | — | DataAnnotations / action | — |
| isDeleted | `bool?` | no | — | DataAnnotations / action | — |
| templateType | `string?` | no | — | DataAnnotations / action | — |
| title | `string?` | no | — | DataAnnotations / action | — |
| name | `string?` | no | — | DataAnnotations / action | — |
| description | `string?` | no | — | DataAnnotations / action | — |
| enNotification | `string?` | no | — | DataAnnotations / action | — |
| swNotification | `string?` | no | — | DataAnnotations / action | — |
| isActive | `bool?` | no | — | DataAnnotations / action | — |
| isSender | `bool?` | no | — | DataAnnotations / action | — |
| isReceiver | `bool?` | no | — | DataAnnotations / action | — |
| darkIcon | `string?` | no | — | DataAnnotations / action | — |
| lightIcon | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "Id": "<Id>", "createdBy": "<createdBy>", "createdDate": "<createdDate>", "updatedBy": "<updatedBy>", "updatedDate": "<updatedDate>", "languageCode": "<languageCode>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `NotificationTemplateController.DeleteNotificationTemplate`
2. Action body in `TZTigoSuperAppNotification/Controllers/NotificationTemplateController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as NotificationTemplateController
  participant Svc as downstream
  App->>Ctrl: POST /api/NotificationTemplate/delete
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
| See service data-model | R/W | Traced at SHA b7c98ec |

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
See `services/notif/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Notification/TZTigoSuperAppNotification/Controllers/NotificationTemplateController.cs › NotificationTemplateController.DeleteNotificationTemplate` @ `b7c98ec`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
