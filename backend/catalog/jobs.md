---
kb_section: backend
type: catalog
ids: [BE-CAT-JOB]
service: ALL
repo: multi
repo_ref: checked-out
repo_sha: multi
updated: 2026-10-05
confidence: confirmed
---

# Jobs catalog

| ID | Service | Kind | Class | Trigger keys | Conf. |
|---|---|---|---|---|---|
| BE-JOB-MERSET-001 | MERSET | BackgroundService | `SchedulerBackgroundWorker` | `Tanzania:ServiceDelayTimeMin`, `Tanzania:MaxRecord` | confirmed |
| BE-JOB-MCHRPT-001 | MCHRPT | BackgroundService | `Worker` | `ServiceDelayTimeMin`, `MaxRecords` | confirmed |
| BE-JOB-MCHRPT-002 | MCHRPT | IHostedService + NCrontab | `InterestCalculationService` | cutoff from `mchangointerestconfiguration` | confirmed |
| BE-JOB-NOTSCH-001 | NOTSCH | BackgroundService | `Worker` | `ServiceDelayTimeMin`, `MaxRecords` | confirmed |
| BE-JOB-NOTIF-001 | NOTIF | see service `jobs.md` | (in-service consumer/worker) | — | partial |

Retired (do not reuse): `BE-JOB-MCHRPT-004` (`ApplicationServiceExtensions` DI registrar).
