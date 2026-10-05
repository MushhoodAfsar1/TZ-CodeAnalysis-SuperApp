---
kb_section: backend
type: service
ids: [BE-SVC-NOTIF]
service: NOTIF
repo: TZ-Tigo-SuperApp-Notification
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: b7c98ec
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-NOTIF TZ-Tigo-SuperApp-Notification
**Repo:** `TZ-Tigo-SuperApp-Notification` · **Type:** service · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `b7c98ec`
**Purpose:** Notifications

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-NOTIF-001 | POST /api/Notifications/create | NotificationsController.CreateNotificationAsync | — | none | confirmed |
| BE-API-NOTIF-002 | POST /api/Notifications/CreatePushNotification | NotificationsController.CreatePushNotificationAsync | — | none | confirmed |
| BE-API-NOTIF-003 | POST /api/Notifications/update | NotificationsController.UpdateNotificationAsync | — | none | confirmed |
| BE-API-NOTIF-004 | POST /api/Notifications/delete | NotificationsController.DeleteNotificationAsync | — | none | confirmed |
| BE-API-NOTIF-005 | POST /api/Notifications/getNotificationHistory | NotificationsController.GetNotificationHistory | — | none | confirmed |
| BE-API-NOTIF-006 | POST /api/Notifications/getall | NotificationsController.GetNotificationsAsync | — | none | confirmed |
| BE-API-NOTIF-007 | POST /api/Notifications/getbyid | NotificationsController.GetNotificationDetails | — | none | confirmed |
| BE-API-NOTIF-008 | GET /api/Notifications/notification-delivery-report | NotificationsController.GetNotificationDeliveryReport | — | none | confirmed |
| BE-API-NOTIF-009 | POST /api/FCMNotification/sendFCMMessage | FCMNotificationController.SendFCMotificationAsync | — | none | confirmed |
| BE-API-NOTIF-010 | POST /api/FCMNotification/UserNotifications | FCMNotificationController.UserNotifications | — | none | confirmed |
| BE-API-NOTIF-011 | POST /api/FCMNotification/SoftDeleteNotifications | FCMNotificationController.SoftDeleteNotifications | — | none | confirmed |
| BE-API-NOTIF-012 | POST /api/FCMNotification/MarkNotificationsAsRead | FCMNotificationController.MarkNotificationsAsRead | — | none | confirmed |
| BE-API-NOTIF-013 | POST /api/NotificationTemplate/getAll | NotificationTemplateController.GetAllNotificationTemplates | — | none | confirmed |
| BE-API-NOTIF-014 | POST /api/NotificationTemplate/create | NotificationTemplateController.CreateNotificationTemplate | — | none | confirmed |
| BE-API-NOTIF-015 | POST /api/NotificationTemplate/updateStatus | NotificationTemplateController.UpdateNotificationStatus | — | none | confirmed |
| BE-API-NOTIF-016 | POST /api/NotificationTemplate/delete | NotificationTemplateController.DeleteNotificationTemplate | — | none | confirmed |
| BE-API-NOTIF-017 | POST /api/NotificationTemplate/updateDetails | NotificationTemplateController.UpdateNotificationTemplateDetails | — | none | confirmed |
| BE-API-NOTIF-018 | GET /api/NotificationTemplate/audit-logs | NotificationTemplateController.GetNotificationTemplateAuditLogs | — | none | confirmed |
| BE-API-NOTIF-019 | POST /api/FCMTemplate/GetFCMTemplate | FCMTemplateController.GetFCMTemplate | — | none | confirmed |


## Dependencies
| Calls | Sync/Async | Why |
|---|---|---|
| Session / Account / Config (typical) | Sync HTTP | Token and profile checks |
| Called by | Sync/Async | Why |
| Mobile app / portal | Sync | User journeys |

## Data owned
| Entity / table | Purpose |
|---|---|
| See data-model.md | — |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`TokenKey`, `isEncrypted`/`is_encrypted`, `Encryption_Decryption_Key`, `IV`, `JwtExpiryMins`, `PostgresConnection` (name only)

## Open questions
Status this run: **inventoried**
