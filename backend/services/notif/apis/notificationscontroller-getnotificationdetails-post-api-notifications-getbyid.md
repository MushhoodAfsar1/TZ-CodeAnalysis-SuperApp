---
kb_section: backend
type: api-contract
ids: [BE-API-NOTIF-007]
service: NOTIF
repo: TZ-Tigo-SuperApp-Notification
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: b7c98ec
updated: 2026-10-05
confidence: confirmed
---
# BE-API-NOTIF-007 NotificationsController.GetNotificationDetails
**Service:** BE-SVC-NOTIF · **Handler:** `TZ-Tigo-SuperApp-Notification/TZTigoSuperAppNotification/Controllers/NotificationController.cs › NotificationsController.GetNotificationDetails` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Notifications/getbyid
  internal_path: /api/Notifications/getbyid
  dispatch_field: null
  dispatch_value: null
  controller_action: NotificationsController.GetNotificationDetails
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| notificationId | `int` | yes | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "notificationId": "<notificationId>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Guard: fetch data successfully | HTTP 200-envelope | — | `TZTigoSuperAppNotification/Controllers/NotificationController.cs › NotificationsController.GetNotificationDetails` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `NotificationsController.GetNotificationDetails`
2. Action body in `TZTigoSuperAppNotification/Controllers/NotificationController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as NotificationsController
  participant Svc as downstream
  App->>Ctrl: POST /api/Notifications/getbyid
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
| — | 200-envelope | — | success=false envelope | fetch data successfully | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/notif/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Notification/TZTigoSuperAppNotification/Controllers/NotificationController.cs › NotificationsController.GetNotificationDetails` @ `b7c98ec`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
