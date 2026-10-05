---
kb_section: backend
type: api-contract
ids: [BE-API-NOTIF-005]
service: NOTIF
repo: TZ-Tigo-SuperApp-Notification
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: b7c98ec
updated: 2026-10-05
confidence: confirmed
---
# BE-API-NOTIF-005 NotificationsController.GetNotificationHistory
**Service:** BE-SVC-NOTIF · **Handler:** `TZ-Tigo-SuperApp-Notification/TZTigoSuperAppNotification/Controllers/NotificationController.cs › NotificationsController.GetNotificationHistory` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Notifications/getNotificationHistory
  internal_path: /api/Notifications/getNotificationHistory
  dispatch_field: null
  dispatch_value: null
  controller_action: NotificationsController.GetNotificationHistory
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
| File | `string?` | no | — | DataAnnotations / action | — |
| FileLocation | `string?` | no | — | DataAnnotations / action | — |
| FileName | `string?` | no | — | DataAnnotations / action | — |
| FileSize | `string?` | no | — | DataAnnotations / action | — |
| NotificationStartString | `string?` | no | — | DataAnnotations / action | — |
| NotificationEndString | `string?` | no | — | DataAnnotations / action | — |
| NotificationStart | `DateTime` | no | — | DataAnnotations / action | — |
| CreatedBy | `string?` | no | — | DataAnnotations / action | — |
| CreatedDate | `DateTime?` | no | — | DataAnnotations / action | — |
| MarkNotificationDelete | `bool?` | no | — | DataAnnotations / action | — |
| MarkNotificationDeleteReason | `string?` | no | — | DataAnnotations / action | — |
| UpdatedBy | `string?` | no | — | DataAnnotations / action | — |
| UpdatedDate | `DateTime?` | no | — | DataAnnotations / action | — |
| englishnotificationtitle | `string?` | no | — | DataAnnotations / action | — |
| englishnotificationdescription | `string?` | no | — | DataAnnotations / action | — |
| sawahinotificationtitle | `string?` | no | — | DataAnnotations / action | — |
| sawahinotificationdescription | `string?` | no | — | DataAnnotations / action | — |
| imageurl | `string?` | no | — | DataAnnotations / action | — |
| imagename | `string?` | no | — | DataAnnotations / action | — |
| imagesize | `string?` | no | — | DataAnnotations / action | — |
| imagetype | `string?` | no | — | DataAnnotations / action | — |
| imagesawahiurl | `string?` | no | — | DataAnnotations / action | — |
| imagesawahiname | `string?` | no | — | DataAnnotations / action | — |
| imagesawahisize | `string?` | no | — | DataAnnotations / action | — |
| imagesawahitype | `string?` | no | — | DataAnnotations / action | — |
| notificationos | `string?` | no | — | DataAnnotations / action | — |
| notificationtype | `string?` | no | — | DataAnnotations / action | — |
| flowid | `string?` | no | — | DataAnnotations / action | — |
| FileId | `int` | no | — | DataAnnotations / action | — |
| msisdn | `string?` | no | — | DataAnnotations / action | — |
| email | `string?` | no | — | DataAnnotations / action | — |
| sms_notification | `string?` | no | — | DataAnnotations / action | — |
| sms_text | `string?` | no | — | DataAnnotations / action | — |
| email_notification | `string?` | no | — | DataAnnotations / action | — |
| email_subject | `string?` | no | — | DataAnnotations / action | — |
| email_text | `string?` | no | — | DataAnnotations / action | — |
| push_notification | `string?` | no | — | DataAnnotations / action | — |
| push_title | `string?` | no | — | DataAnnotations / action | — |
| push_text | `string?` | no | — | DataAnnotations / action | — |
| push_template | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "Id": "<Id>", "File": "<File>", "FileLocation": "<FileLocation>", "FileName": "<FileName>", "FileSize": "<FileSize>", "NotificationStartString": "<NotificationStartString>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Guard: saved successfully | HTTP 200-envelope | — | `TZTigoSuperAppNotification/Controllers/NotificationController.cs › NotificationsController.GetNotificationHistory` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `NotificationsController.GetNotificationHistory`
2. Action body in `TZTigoSuperAppNotification/Controllers/NotificationController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as NotificationsController
  participant Svc as downstream
  App->>Ctrl: POST /api/Notifications/getNotificationHistory
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
| — | 200-envelope | — | success=false envelope | saved successfully | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/notif/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Notification/TZTigoSuperAppNotification/Controllers/NotificationController.cs › NotificationsController.GetNotificationHistory` @ `b7c98ec`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
