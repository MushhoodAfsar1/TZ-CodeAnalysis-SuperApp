---
kb_section: backend
type: service
ids: [BE-SVC-NOTSCH]
service: NOTSCH
repo: TZ-Tigo-SuperApp-Notification-Scheduler
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 72838eb
updated: 2026-10-05
confidence: partial
---

# Data model — NOTSCH

| Entity | Table | Source |
|---|---|---|
| `NotificationTemplates` | `—` | `TZTigoSuperAppNotificationScheduler/Domain/Enums/NotificationTemplates.cs` |
| `FCMTemplates` | `—` | `TZTigoSuperAppNotificationScheduler/Domain/Enums/FCMTemplates.cs` |
| `StringEnum` | `—` | `TZTigoSuperAppNotificationScheduler/Domain/Enums/FCMTemplates.cs` |
| `notificationtemplates` | `—` | `TZTigoSuperAppNotificationScheduler/Domain/Entities/NotificationTemplates.cs` |
| `templatetranslation` | `—` | `TZTigoSuperAppNotificationScheduler/Domain/Entities/NotificationTemplates.cs` |
| `PushNotificationHeaders` | `—` | `TZTigoSuperAppNotificationScheduler/Domain/Entities/NotificationTemplates.cs` |
| `notificationdetail` | `—` | `TZTigoSuperAppNotificationScheduler/Domain/Entities/NotificationDetail.cs` |
| `notification` | `—` | `TZTigoSuperAppNotificationScheduler/Domain/Entities/Notification.cs` |
| `fcmnotificationhistory` | `—` | `TZTigoSuperAppNotificationScheduler/Domain/Entities/FCMNotificationHistory.cs` |
| `fcmdeviceinfo` | `—` | `TZTigoSuperAppNotificationScheduler/Domain/Entities/FCMDeviceInfo.cs` |
| `NotificationContextEF` | `—` | `TZTigoSuperAppNotificationScheduler/Domain/Contexts/NotificationContextEF.cs` |
| `notificationstatus` | `—` | `TZTigoSuperAppNotificationScheduler/Domain/Entities/Lookup/NotificationStatus.cs` |
| `PushNotification` | `—` | `TZTigoSuperAppNotificationScheduler/Domain/DTOs/Responses/PushNotification.cs` |
| `HMSNotificationResponse` | `—` | `TZTigoSuperAppNotificationScheduler/Domain/DTOs/Responses/PushNotification.cs` |
| `GenericResponseModel` | `—` | `TZTigoSuperAppNotificationScheduler/Domain/DTOs/BaseResponseModel/GenericResponseModel.cs` |
| `ErrorResponseDto` | `—` | `TZTigoSuperAppNotificationScheduler/Domain/DTOs/BaseResponseModel/ErrorResponseDto.cs` |
| `BaseResponse` | `—` | `TZTigoSuperAppNotificationScheduler/Domain/DTOs/BaseResponseModel/BaseResponse.cs` |
| `ResponseCode` | `—` | `TZTigoSuperAppNotificationScheduler/Domain/DTOs/BaseResponseModel/ResponseCodeResponse.cs` |
| `FCMNotification` | `—` | `TZTigoSuperAppNotificationScheduler/Domain/DTOs/Requests/FCMNotification.cs` |
| `NotificationTemplate` | `—` | `TZTigoSuperAppNotificationScheduler/Domain/DTOs/Requests/FCMNotification.cs` |
| `HMSToken` | `—` | `TZTigoSuperAppNotificationScheduler/Domain/DTOs/Requests/HMSToken.cs` |
