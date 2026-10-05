---
kb_section: backend
type: service
ids: [BE-JOB-MCHRPT-001, BE-JOB-MCHRPT-002]
service: MCHRPT
repo: TZ-Tigo-SuperApp-MChangoReportScheduler
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 34ba77f
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-MCHRPT jobs

| ID | Trigger | What it does | Data / downstream | Conf. |
|---|---|---|---|---|
| BE-JOB-MCHRPT-001 | `Worker` BackgroundService loop | `IReportSendingService.SendReportToRecipient(MaxRecords)` | report recipients | confirmed |
| BE-JOB-MCHRPT-002 | `InterestCalculationService` hosted | Interest calculation for MChango | MChango data | partial |

Delay: `ServiceDelayTimeMin` minutes between loops (`60000 * ServiceDelayTimeMin`). Batch size: `MaxRecords`.

Evidence: `TZTigoSuperAppMChangoReportScheduler/Worker.cs › ExecuteAsync`
