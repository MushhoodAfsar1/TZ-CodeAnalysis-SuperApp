---
kb_section: backend
type: service
ids: [BE-SVC-NOTIF]
service: NOTIF
repo: TZ-Tigo-SuperApp-Notification
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: b7c98ec
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-NOTIF Notifications and FCM
**Repo:** `TZ-Tigo-SuperApp-Notification` · **Type:** service · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `b7c98ec`
**Purpose:** Notifications and FCM

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** MassTransit, MassTransit.RabbitMQ, Microsoft.AspNetCore.Authentication.JwtBearer, Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-NOTIF-001 | `POST /api/FCMNotification/sendFCMMessage` | `FCMNotificationController.SendFCMotificationAsync` | FCMNotificationController.SendFCMotificationAsync | see contract | confirmed |
| BE-API-NOTIF-002 | `POST /api/FCMNotification/UserNotifications` | `FCMNotificationController.UserNotifications` | FCMNotificationController.UserNotifications | see contract | confirmed |
| BE-API-NOTIF-003 | `POST /api/FCMNotification/SoftDeleteNotifications` | `FCMNotificationController.SoftDeleteNotifications` | FCMNotificationController.SoftDeleteNotifications | see contract | confirmed |
| BE-API-NOTIF-004 | `POST /api/FCMNotification/MarkNotificationsAsRead` | `FCMNotificationController.MarkNotificationsAsRead` | FCMNotificationController.MarkNotificationsAsRead | see contract | confirmed |
| BE-API-NOTIF-005 | `POST /api/Notifications/create` | `NotificationsController.CreateNotificationAsync` | NotificationsController.CreateNotificationAsync | see contract | confirmed |
| BE-API-NOTIF-006 | `POST /api/Notifications/CreatePushNotification` | `NotificationsController.CreatePushNotificationAsync` | NotificationsController.CreatePushNotificationAsync | see contract | confirmed |
| BE-API-NOTIF-007 | `POST /api/Notifications/update` | `NotificationsController.UpdateNotificationAsync` | NotificationsController.UpdateNotificationAsync | see contract | confirmed |
| BE-API-NOTIF-008 | `POST /api/Notifications/delete` | `NotificationsController.DeleteNotificationAsync` | NotificationsController.DeleteNotificationAsync | see contract | confirmed |
| BE-API-NOTIF-009 | `POST /api/Notifications/getNotificationHistory` | `NotificationsController.GetNotificationHistory` | NotificationsController.GetNotificationHistory | see contract | confirmed |
| BE-API-NOTIF-010 | `POST /api/Notifications/getall` | `NotificationsController.GetNotificationsAsync` | NotificationsController.GetNotificationsAsync | see contract | confirmed |
| BE-API-NOTIF-011 | `POST /api/Notifications/getbyid` | `NotificationsController.GetNotificationDetails` | NotificationsController.GetNotificationDetails | see contract | confirmed |
| BE-API-NOTIF-012 | `GET /api/Notifications/notification-delivery-report` | `NotificationsController.GetNotificationDeliveryReport` | NotificationsController.GetNotificationDeliveryReport | see contract | confirmed |
| BE-API-NOTIF-013 | `POST /api/FCMTemplate/GetFCMTemplate` | `FCMTemplateController.GetFCMTemplate` | FCMTemplateController.GetFCMTemplate | see contract | confirmed |
| BE-API-NOTIF-014 | `POST /api/NotificationTemplate/getAll` | `NotificationTemplateController.GetAllNotificationTemplates` | NotificationTemplateController.GetAllNotificationTemplates | see contract | confirmed |
| BE-API-NOTIF-015 | `POST /api/NotificationTemplate/create` | `NotificationTemplateController.CreateNotificationTemplate` | NotificationTemplateController.CreateNotificationTemplate | see contract | confirmed |
| BE-API-NOTIF-016 | `POST /api/NotificationTemplate/updateStatus` | `NotificationTemplateController.UpdateNotificationStatus` | NotificationTemplateController.UpdateNotificationStatus | see contract | confirmed |
| BE-API-NOTIF-017 | `POST /api/NotificationTemplate/delete` | `NotificationTemplateController.DeleteNotificationTemplate` | NotificationTemplateController.DeleteNotificationTemplate | see contract | confirmed |
| BE-API-NOTIF-018 | `POST /api/NotificationTemplate/updateDetails` | `NotificationTemplateController.UpdateNotificationTemplateDetails` | NotificationTemplateController.UpdateNotificationTemplateDetails | see contract | confirmed |
| BE-API-NOTIF-019 | `GET /api/NotificationTemplate/audit-logs` | `NotificationTemplateController.GetNotificationTemplateAuditLogs` | NotificationTemplateController.GetNotificationTemplateAuditLogs | see contract | confirmed |

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
| `BaseResponse` / `—` | `TZTigoSuperAppNotification/Domain/App/BaseResponse.cs` |
| `AuditLogsRequest` / `—` | `TZTigoSuperAppNotification/Domain/App/AuditLogsRequest.cs` |
| `CloudStorage` / `—` | `TZTigoSuperAppNotification/Domain/Implementation/CloudStorage.cs` |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`AzureBlobStorage`, `AzureBlobStorage:NotificationContainer`, `ConnectionStringNotification:<redacted-purpose>`, `DBServerUrl`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `EnableLog:Warning`, `Encryption_Decryption_Key`, `Encryption_Decryption_Key_V2`, `IV`, `IV_V2`, `NotificationContainer`, `Origins`, `PushNotification:<redacted-purpose>`, `PushNotification:FCM:ServiceAccountJson`, `PushNotification:FCM:ServiceAccountPath`, `PushNotification:FCM:Token`, `PushNotification:FCM:Url`, `PushNotification:FCM:image`, `PushNotification:HMS:ClientId`, `PushNotification:HMS:GrantType`, `PushNotification:HMS:SendMessage:Method`, `PushNotification:HMS:SendMessage:Url`, `PushNotification:HMS:SendMessage:Version`, `PushNotification:HMS:TokenUrl`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:LogQueueName`, `RabbitMQ:LogURL`, `RabbitMQ:QueueName`, `RabbitMQ:Username`, `SaveLogs`, `SendAuditLogsViaService`, `TempServerUrl`, `UploadOnAzureStorage`, `isEncrypted`

## Open questions
- Gateway public URLs not in-repo.
