---
kb_section: backend
type: api-contract
ids: [BE-API-NOTIF-009]
service: NOTIF
repo: TZ-Tigo-SuperApp-Notification
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: b7c98ec
updated: 2026-10-05
confidence: confirmed
---
# BE-API-NOTIF-009 FCMNotificationController.SendFCMotificationAsync
**Service:** BE-SVC-NOTIF · **Handler:** `TZ-Tigo-SuperApp-Notification/TZTigoSuperAppNotification/Controllers/FCMNotificationController.cs › FCMNotificationController.SendFCMotificationAsync` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/FCMNotification/sendFCMMessage
  internal_path: /api/FCMNotification/sendFCMMessage
  dispatch_field: null
  dispatch_value: null
  controller_action: FCMNotificationController.SendFCMotificationAsync
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| request | `Shared.Entities.FCM.FCMNotificationRequest` | unknown | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "request": "<request>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Guard: sent successfully | HTTP 200-envelope | — | `TZTigoSuperAppNotification/Controllers/FCMNotificationController.cs › FCMNotificationController.SendFCMotificationAsync` |
| 2 | Guard: some error occurred | HTTP 200-envelope | — | `TZTigoSuperAppNotification/Controllers/FCMNotificationController.cs › FCMNotificationController.SendFCMotificationAsync` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `FCMNotificationController.SendFCMotificationAsync`
2. Action body in `TZTigoSuperAppNotification/Controllers/FCMNotificationController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as FCMNotificationController
  participant Svc as downstream
  App->>Ctrl: POST /api/FCMNotification/sendFCMMessage
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
| — | 200-envelope | — | success=false envelope | sent successfully | no |
| — | 200-envelope | — | success=false envelope | some error occurred | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/notif/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Notification/TZTigoSuperAppNotification/Controllers/FCMNotificationController.cs › FCMNotificationController.SendFCMotificationAsync` @ `b7c98ec`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
