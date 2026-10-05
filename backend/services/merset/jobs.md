---
kb_section: backend
type: service
ids: [BE-SVC-MERSET, BE-JOB-MERSET-001]
service: MERSET
repo: TZ-Tigo-SuperApp-MerchantSettlementScheduler
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: d638213
updated: 2026-10-05
confidence: confirmed
---

# Jobs — MERSET

No Hangfire/Quartz. One hosted `BackgroundService`.

| ID | Kind | Class | File | Notes |
|---|---|---|---|---|
| BE-JOB-MERSET-001 | BackgroundService | `SchedulerBackgroundWorker` | `TZTigoSuperAppMerchantSettlementScheduler/SchedulerBackgroundWorker.cs` | Settlement loop. `HostOptions.BackgroundServiceExceptionBehavior = Ignore`. |

`Helpers/ConfigurationExtensions.cs` is DI/config only — **not a job**.

## BE-JOB-MERSET-001 SchedulerBackgroundWorker

**Trigger:** process lifetime. Delay key `Tanzania:ServiceDelayTimeMin` (minutes × 60000). Batch `Tanzania:MaxRecord`.

**Steps:**
1. `ExecuteAsync` loop → `GenerateParallelTask(limit)`.
2. Transaction `IsolationLevel.RepeatableRead`: read due `schedule` (`!IsDeleted`, `status==1`, `isactive`, `nextexecutiondate` null or due), `Take(MaxRecord)`.
3. For each: set `lastexecutiondate` / `nextexecutiondate` via `SettlementScheduleService.CalculateNextExecutionTimeAsync` (scheduletype 0/1/2); write `schedule`; commit.
4. Parallel `UpdateRecordStatusAsync`: read active `schedulesubscriber`.
5. Per subscriber: SOAP balance → fee/query → payment by `paymenttype` (`0` full / `1` fixed / `2` %) and `operationtype` (WALLET_BANK uses bank URL keys); write `transaction` and `islasttransactionsuccessful`; FCM on success.

**Checks:** empty set → skip. Concurrent transaction → log `InvalidOperationException` and rollback. Per-subscriber failure rolls back that subscriber then forces `islasttransactionsuccessful=false`. FCM failures do not undo payment.

**Data:** R/W `schedule`, R/W `schedulesubscriber`, W `transaction`. Conn key `ConnectionStrings:MerchantSettlementConnection` / env `MerchantSettlementConnection`.

**Downstream (keys only):**
- Balance POST `Tanzania:SuperAppMTPGGetBalance` + `Tanzania:ConsumerID`, `Tanzania:ChannelUser`, `Tanzania:ChannelPass`, `Tanzania:TerminalType`
- Fee/query `Tanzania:SuperAppMTPGBillQuery` or WALLET_BANK `Tanzania:BankTransferFee`; `Tanzania:FeeSourcePIN`, `Tanzania:FeeTerminalType`, `Tanzania:ShortCode`, `Tanzania:BankTransferShortCode`
- Payment `Tanzania:SuperAppMTPGPayment` or `Tanzania:BankTransferPayment`; `Tanzania:PaymentTerminalType`, `Tanzania:PaymentTypeProxy` / `Tanzania:PaymentType`
- FCM: if `SendFCMViaService=="1"` → HTTP `FCMNotify`; else RabbitMQ `RabbitMQ:URL|Port|Username|Password|IsHttpsRabbitMQ|QueueName`
- Named HttpClient `CMM` base `ConfigAPIUrl` (registered; not on main settle path)

**Side effects:** MMP money move; FCM template `ReceiverSendMoney`; schedule next-run stamps.

**Evidence:** `TZ-Tigo-SuperApp-MerchantSettlementScheduler/TZTigoSuperAppMerchantSettlementScheduler/SchedulerBackgroundWorker.cs › SchedulerBackgroundWorker.ExecuteAsync` / `GenerateParallelTask` / `UpdateRecordStatusAsync` @ `d638213`; `SettlementScheduleRepository.GetBalance` / `FinalizeTransaction` / `SubmitBillPayment`; `FCMService.SendPushNotification`.
