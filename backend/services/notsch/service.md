---
kb_section: backend
type: service
ids: [BE-SVC-NOTSCH]
service: NOTSCH
repo: TZ-Tigo-SuperApp-Notification-Scheduler
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 72838eb
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-NOTSCH Notification delivery scheduler
**Repo:** `TZ-Tigo-SuperApp-Notification-Scheduler` · **Type:** batch/scheduler · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `72838eb`
**Purpose:** Notification delivery scheduler

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** FluentValidation, FluentValidation.AspNetCore, Microsoft.AspNetCore.Authentication.JwtBearer, Microsoft.AspNetCore.Identity.EntityFrameworkCore, Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, RabbitMQ.Client, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|

## Dependencies
| Calls | Sync/Async | Why |
|---|---|---|
| CONFIG `CMM` / `ConfigAPIUrl` | Sync | response-code mapping, catalogues |

| Called by | Sync/Async | Why |
|---|---|---|
| Mobile app (direct or via external gateway) | Sync | product APIs |
| WebPortal | Sync | admin screens (IDENT/CONFIG mainly) |

## Data owned
| Entity / table | Purpose |
|---|---|
| `NotificationTemplates` / `—` | `TZTigoSuperAppNotificationScheduler/Domain/Enums/NotificationTemplates.cs` |
| `FCMTemplates` / `—` | `TZTigoSuperAppNotificationScheduler/Domain/Enums/FCMTemplates.cs` |
| `StringEnum` / `—` | `TZTigoSuperAppNotificationScheduler/Domain/Enums/FCMTemplates.cs` |
| `notificationtemplates` / `—` | `TZTigoSuperAppNotificationScheduler/Domain/Entities/NotificationTemplates.cs` |
| `templatetranslation` / `—` | `TZTigoSuperAppNotificationScheduler/Domain/Entities/NotificationTemplates.cs` |
| `PushNotificationHeaders` / `—` | `TZTigoSuperAppNotificationScheduler/Domain/Entities/NotificationTemplates.cs` |
| `notificationdetail` / `—` | `TZTigoSuperAppNotificationScheduler/Domain/Entities/NotificationDetail.cs` |
| `notification` / `—` | `TZTigoSuperAppNotificationScheduler/Domain/Entities/Notification.cs` |
| `fcmnotificationhistory` / `—` | `TZTigoSuperAppNotificationScheduler/Domain/Entities/FCMNotificationHistory.cs` |
| `fcmdeviceinfo` / `—` | `TZTigoSuperAppNotificationScheduler/Domain/Entities/FCMDeviceInfo.cs` |
| `NotificationContextEF` / `—` | `TZTigoSuperAppNotificationScheduler/Domain/Contexts/NotificationContextEF.cs` |
| `notificationstatus` / `—` | `TZTigoSuperAppNotificationScheduler/Domain/Entities/Lookup/NotificationStatus.cs` |
| `PushNotification` / `—` | `TZTigoSuperAppNotificationScheduler/Domain/DTOs/Responses/PushNotification.cs` |
| `HMSNotificationResponse` / `—` | `TZTigoSuperAppNotificationScheduler/Domain/DTOs/Responses/PushNotification.cs` |
| `GenericResponseModel` / `—` | `TZTigoSuperAppNotificationScheduler/Domain/DTOs/BaseResponseModel/GenericResponseModel.cs` |
| `ErrorResponseDto` / `—` | `TZTigoSuperAppNotificationScheduler/Domain/DTOs/BaseResponseModel/ErrorResponseDto.cs` |
| `BaseResponse` / `—` | `TZTigoSuperAppNotificationScheduler/Domain/DTOs/BaseResponseModel/BaseResponse.cs` |
| `ResponseCode` / `—` | `TZTigoSuperAppNotificationScheduler/Domain/DTOs/BaseResponseModel/ResponseCodeResponse.cs` |
| `FCMNotification` / `—` | `TZTigoSuperAppNotificationScheduler/Domain/DTOs/Requests/FCMNotification.cs` |
| `NotificationTemplate` / `—` | `TZTigoSuperAppNotificationScheduler/Domain/DTOs/Requests/FCMNotification.cs` |
| `HMSToken` / `—` | `TZTigoSuperAppNotificationScheduler/Domain/DTOs/Requests/HMSToken.cs` |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `EnableLog:Warning`, `Encryption_Decryption_Key`, `IV`, `MaxRecords`, `PushNotification:<redacted-purpose>`, `PushNotification:HMS:ClientId`, `PushNotification:HMS:GrantType`, `PushNotification:HMS:SendMessage:Method`, `PushNotification:HMS:SendMessage:Url`, `PushNotification:HMS:SendMessage:Version`, `PushNotification:HMS:TokenUrl`, `ServiceDelayTimeMin`

## Open questions
- Gateway public URLs not in-repo.
