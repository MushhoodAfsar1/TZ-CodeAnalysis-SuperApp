---
kb_section: backend
type: service
ids: [BE-SVC-MERSET]
service: MERSET
repo: TZ-Tigo-SuperApp-MerchantSettlementScheduler
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: d638213
updated: 2026-10-05
confidence: partial
---

# Jobs — MERSET

| ID | Kind | Class | File | Notes |
|---|---|---|---|---|
| BE-JOB-MERSET-001 | BackgroundService | `SchedulerBackgroundWorker` | `TZTigoSuperAppMerchantSettlementScheduler/SchedulerBackgroundWorker.cs` | Loop: `ExecuteAsync` → `GenerateParallelTask(Tanzania:MaxRecord)` then delay `Tanzania:ServiceDelayTimeMin` minutes. |

## BE-JOB-MERSET-001 SchedulerBackgroundWorker
**Trigger:** hosted `BackgroundService` while process is up (delay config, not cron).
**Steps:**
1. Open `TZMerchantContext` transaction `IsolationLevel.RepeatableRead`.
2. Read `schedule` where not deleted, `status==1`, `isactive`, `nextexecutiondate` null or due; `Take(MaxRecord)` ordered by id.
3. For each row, set `lastexecutiondate=now` and `nextexecutiondate` via `ISettlementScheduleService.CalculateNextExecutionTimeAsync`.
4. `SaveChanges` + commit; then `UpdateRecordStatusAsync` per schedule (FCM possible).
**Checks:** empty set → skip. Concurrent transaction → log `InvalidOperationException`.
**Data:** `schedule` table R/W.
**Config keys:** `Tanzania:MaxRecord`, `Tanzania:ServiceDelayTimeMin`.
**Evidence:** `TZ-Tigo-SuperApp-MerchantSettlementScheduler/TZTigoSuperAppMerchantSettlementScheduler/SchedulerBackgroundWorker.cs › ExecuteAsync` @ `d638213`.
