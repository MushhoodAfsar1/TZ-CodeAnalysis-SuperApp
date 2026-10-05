---
kb_section: backend
type: service
ids: [BE-JOB-MERSET-001]
service: MERSET
repo: TZ-Tigo-SuperApp-MerchantSettlementScheduler
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: d638213
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-MERSET jobs

| ID | Trigger | What it does | Data / downstream | Conf. |
|---|---|---|---|---|
| BE-JOB-MERSET-001 | `SchedulerBackgroundWorker` loop (`BackgroundService`) | Runs merchant settlement schedule processing | `ISettlementScheduleService`, FCM, merchant EF | confirmed |

Evidence: `TZTigoSuperAppMerchantSettlementScheduler/SchedulerBackgroundWorker.cs › ExecuteAsync`

Config key names only: delay/interval keys in worker body (not recorded as values).
