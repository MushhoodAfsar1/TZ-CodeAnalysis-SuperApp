---
kb_section: backend
type: service
ids: [BE-SVC-NOTSCH, BE-JOB-NOTSCH-001]
service: NOTSCH
repo: TZ-Tigo-SuperApp-Notification-Scheduler
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 72838eb
updated: 2026-10-05
confidence: confirmed
---

# Jobs — NOTSCH

No Hangfire/Quartz. `SendNotifications` is a scoped worker of `Worker`, not a separate hosted job.

| ID | Kind | Class | File | Notes |
|---|---|---|---|---|
| BE-JOB-NOTSCH-001 | BackgroundService | `Worker` | `TZTigoSuperAppNotificationScheduler/Worker.cs` | Bulk FCM/HMS send loop. |

## BE-JOB-NOTSCH-001 Worker

**Trigger:** host lifetime. Delay `ServiceDelayTimeMin`. Batch `MaxRecords`. Firebase Admin initialized in Program (embedded service-account JSON — no config key). Conn `ConnectionStrings:NotificationManagement` / env `NotificationManagement`.

**Steps:**
1. `SendBulkNotifications(limit)` — read unprocessed `notification` (`isnotificationprocessed != true`, `notificationstartdatetime <= now`).
2. Per notification `TriggerNotifications`: chunk `notificationdetail` (SQL DISTINCT ON msisdn, 10k); batches of 495, concurrency 2.
3. Read `fcmdeviceinfo` (channel `AXIANSUPERAPP`, not deleted); build FCM/HMS payloads.
4. `FCMNotificationRepository.SendPushNotificationAsync` — FCM multicast; HMS token+send HTTP.
5. Write `notificationdetail` (`sendmessage`, `sendstatus`, `updateddate`); write FCM history; finally mark `notification` processed + end time.

**Data:** R/W `notification`, `notificationdetail`; R `fcmdeviceinfo`; W `fcmnotificationhistory`.

**Downstream:**
- FCM: Firebase Admin SDK (`PushNotification:FCM:*` keys unused in C#)
- HMS: `PushNotification:HMS:TokenUrl`, `GrantType`, `ClientId`, `ClientSecret`, `SendMessage:Url`, `SendMessage:Version`, `SendMessage:Method`

**Errors / side effects:** outer/batch catch+log (continues); marks notification processed even if some batches failed; FCM + HMS pushes.

**Evidence:** `TZ-Tigo-SuperApp-Notification-Scheduler/TZTigoSuperAppNotificationScheduler/Worker.cs › Worker.ExecuteAsync` @ `72838eb`; `.../Services/SendNotifications.cs › SendBulkNotifications` / `TriggerNotifications`; `.../Repository/FCMNotificationRepository.cs › SendPushNotificationAsync`.
