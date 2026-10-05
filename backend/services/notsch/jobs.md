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

# Jobs — NOTSCH

| ID | Kind | Class | File | Notes |
|---|---|---|---|---|
| BE-JOB-NOTSCH-001 | BackgroundService | `Worker` | `TZTigoSuperAppNotificationScheduler/Worker.cs` | Polls `ISendNotifications` in a loop. |

## BE-JOB-NOTSCH-001 Worker
**Trigger:** `BackgroundService` host lifetime.
**Steps:** `ExecuteAsync` loop delegates to notification send service (queued/outbox style inside NOTSCH). Downstream: NOTIF / FCM (hosts omitted).
**Evidence:** `TZ-Tigo-SuperApp-Notification-Scheduler/TZTigoSuperAppNotificationScheduler/Worker.cs › Worker` @ `72838eb`.
