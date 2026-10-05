---
kb_section: backend
type: api-contract
ids: [BE-API-NOTIF-009]
service: NOTIF
repo: TZ-Tigo-SuperApp-Notification
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: b7c98ec
updated: 2026-10-05
confidence: confirmed
---

# BE-API-NOTIF-009 NotificationsController.GetNotificationHistory
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
- **Method / path:** `POST /api/Notifications/getNotificationHistory`
- **Auth / filters:** none on action (pipeline may still authorize)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `Id` | `int` | N | — | shape only | Id |
| `File` | `string?` | N | — | shape only | File |
| `FileLocation` | `string?` | N | — | shape only | FileLocation |
| `FileName` | `string?` | N | — | shape only | FileName |
| `FileSize` | `string?` | N | — | shape only | FileSize |
| `NotificationStartString` | `string?` | N | — | shape only | NotificationStartString |
| `NotificationEndString` | `string?` | N | — | shape only | NotificationEndString |
| `NotificationStart` | `DateTime` | N | — | shape only | NotificationStart |
| `CreatedBy` | `string?` | N | — | shape only | CreatedBy |
| `CreatedDate` | `DateTime?` | N | — | shape only | CreatedDate |
| `MarkNotificationDelete` | `bool?` | N | — | shape only | MarkNotificationDelete |
| `MarkNotificationDeleteReason` | `string?` | N | — | shape only | MarkNotificationDeleteReason |
| `UpdatedBy` | `string?` | N | — | shape only | UpdatedBy |
| `UpdatedDate` | `DateTime?` | N | — | shape only | UpdatedDate |
| `englishnotificationtitle` | `string?` | N | — | shape only | englishnotificationtitle |
| `englishnotificationdescription` | `string?` | N | — | shape only | englishnotificationdescription |
| `sawahinotificationtitle` | `string?` | N | — | shape only | sawahinotificationtitle |
| `sawahinotificationdescription` | `string?` | N | — | shape only | sawahinotificationdescription |
| `imageurl` | `string?` | N | — | shape only | imageurl |
| `imagename` | `string?` | N | — | shape only | imagename |
| `imagesize` | `string?` | N | — | shape only | imagesize |
| `imagetype` | `string?` | N | — | shape only | imagetype |
| `imagesawahiurl` | `string?` | N | — | shape only | imagesawahiurl |
| `imagesawahiname` | `string?` | N | — | shape only | imagesawahiname |
| `imagesawahisize` | `string?` | N | — | shape only | imagesawahisize |
| `imagesawahitype` | `string?` | N | — | shape only | imagesawahitype |
| `notificationos` | `string?` | N | — | shape only | notificationos |
| `notificationtype` | `string?` | N | — | shape only | notificationtype |
| `flowid` | `string?` | N | — | shape only | flowid |

Headers / route / query params: none parsed beyond action signature `[('request', 'NotificationRequest')]`

Sample (synthetic):
```json
{
  "Id": 0,
  "File": "<string>",
  "FileLocation": "<string>",
  "FileName": "<string>",
  "FileSize": "<string>",
  "NotificationStartString": "<string>",
  "NotificationEndString": "<string>",
  "NotificationStart": "<iso-datetime>",
  "CreatedBy": "<string>",
  "CreatedDate": "<iso-datetime>",
  "MarkNotificationDelete": false,
  "MarkNotificationDeleteReason": "<string>",
  "UpdatedBy": "<string>",
  "UpdatedDate": "<iso-datetime>",
  "englishnotificationtitle": "<string>",
  "englishnotificationdescription": "<string>",
  "sawahinotificationtitle": "<string>",
  "sawahinotificationdescription": "<string>",
  "imageurl": "<string>",
  "imagename": "<string>",
  "imagesize": "<string>",
  "imagetype": "<string>",
  "imagesawahiurl": "<string>",
  "imagesawahiname": "<string>",
  "imagesawahisize": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `request == null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Notification/TZTigoSuperAppNotification/Controllers/NotificationController.cs › NotificationsController.GetNotificationHistory` |
| 2 | `request.Id == 0` | branch / error envelope | — | `TZ-Tigo-SuperApp-Notification/TZTigoSuperAppNotification/Controllers/NotificationController.cs › NotificationsController.GetNotificationHistory` |
| 3 | `notifications.Any(` | branch / error envelope | — | `TZ-Tigo-SuperApp-Notification/TZTigoSuperAppNotification/Controllers/NotificationController.cs › NotificationsController.GetNotificationHistory` |

## Internal call chain
1. Client POST `/api/Notifications/getNotificationHistory`.
2. `NotificationsController.GetNotificationHistory` runs (`TZ-Tigo-SuperApp-Notification/TZTigoSuperAppNotification/Controllers/NotificationController.cs`).
3. Calls `_notificationRepository.GetNotificationHistory`.
4. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>NotificationsController: POST /api/Notifications/getNotificationHistory
  participant NotificationsController
  NotificationsController->>_notificationRepository: GetNotificationHistory()
```

## Downstream
| Order | Target (BE-API / BE-INT / BE-EVT) | Sync/Async | Condition | Sent / used fields |
|---|---|---|---|---|
| — | none parsed beyond in-process services | — | — | — |

## Data touched
| Entity / table / SP | R/W | Notes |
|---|---|---|
| see service `data-model.md` | mixed | not fully attributed per action |

## Response (decrypted)
| Field (JSON) | Type | Always / when | Meaning |
|---|---|---|---|
| `success` | boolean | always | handler outcome |
| `responseCode` | string | always | mapped via CONFIG when handler used |
| `transactionStatus` | string | success | mapped message |
| `errorDescription` | string | failure | mapped or static |
| `appVersionInfo` | string | often | app version hint |
| `responseData` | object | success | action-specific |

Sample (synthetic):
```json
{
  "success": true,
  "responseCode": "<code>",
  "transactionStatus": "<message>",
  "appVersionInfo": "<version>",
  "responseData": {}
}
```

## Errors
| BE code | HTTP | ID | Condition | Message key/text | Retryable |
|---|---|---|---|---|---|
| 500 | 500 | BE-ERR-NOTIF-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-NOTIF-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-NOTIF-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-Notification/TZTigoSuperAppNotification/Controllers/NotificationController.cs › NotificationsController.GetNotificationHistory` @ `b7c98ec`
- Decrypted DTO `NotificationRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
