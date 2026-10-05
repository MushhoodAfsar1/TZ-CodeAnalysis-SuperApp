---
kb_section: backend
type: service
ids: [BE-JOB-NOTSCH-001]
service: NOTSCH
repo: TZ-Tigo-SuperApp-Notification-Scheduler
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 72838eb
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-NOTSCH jobs

| ID | Trigger | What it does | Data / downstream | Conf. |
|---|---|---|---|---|
| BE-JOB-NOTSCH-001 | `Worker` BackgroundService loop | `ISendNotifications.SendBulkNotifications(MaxRecords)` | notification outbox / NOTIF | confirmed |

Delay: `ServiceDelayTimeMin` minutes. Batch: `MaxRecords`.

Evidence: `TZTigoSuperAppNotificationScheduler/Worker.cs › ExecuteAsync`
