---
kb_section: backend
type: service
ids: [BE-SVC-MCHRPT, BE-JOB-MCHRPT-001, BE-JOB-MCHRPT-002]
service: MCHRPT
repo: TZ-Tigo-SuperApp-MChangoReportScheduler
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 34ba77f
updated: 2026-10-05
confidence: confirmed
---

# Jobs — MCHRPT

No Hangfire/Quartz. Two executable hosted jobs. **`ApplicationServiceExtensions` is not a job** (DI registrar that mentions `BackgroundService` in source). `ReportSendingService` is a scoped worker of `Worker`, not separately hosted.

| ID | Kind | Class | File | Notes |
|---|---|---|---|---|
| BE-JOB-MCHRPT-001 | BackgroundService | `Worker` | `TZTigoSuperAppMChangoReportScheduler/Worker.cs` | Report email loop. Delegates to `ReportSendingService`. |
| BE-JOB-MCHRPT-002 | IHostedService + NCrontab Timer | `InterestCalculationService` | `.../Services/BackgroundService/InterestCalculationService.cs` | Cutoff cron from CONFIG interest table. |
| ~~BE-JOB-MCHRPT-004~~ | *(removed — false positive)* | `ApplicationServiceExtensions` | `.../Common/Extensions/ApplicationServiceExtensions.cs` | ID retired; do not reuse. |

## BE-JOB-MCHRPT-001 Worker / report sending

**Trigger:** host lifetime. Delay `ServiceDelayTimeMin`. Batch `MaxRecords`.

**Steps:**
1. Scope → `IReportSendingService.SendReportToRecipient`.
2. Redis lock `CacheKeys.MChangoReportsKey` (`"report"`); skip if held; set ~60m; clear in finally.
3. Read pending `MchangoReportRequests` (limit); empty → unlock+return.
4. Per request: date range from `ReportTimePeriod` → load Account / Statement / GroupBalance from Account, PledgeTransaction, TransactionHistory, Invitation. GroupBalance/PDF header also SOAP balance.
5. No data → write status `Done` + no-data email; else excel/pdf → SMTP; on success write `Done`.

**Data:** R/W `MchangoReportRequests`; R `Account`, `PledgeTransaction`, `TransactionHistory`, `Invitation`. Redis keys `RedisURL`, `RedisPassword`, `IsRedisCluster`. Conn `ConnectionStrings:DefaultConnection`.

**Downstream:** SMTP `SmtpServer`, `SmtpPort`, `SmtpUsername`, `SmtpPassword`, `EmailCC`. Balance SOAP `GetBalance` + `Tanzania:SendMoneyFeeCheck:ConsumerID:APP`, `Tanzania:ChannelUser`, `Tanzania:ChannelPassword`. PDF assets `MChangoImage`, `MIXXLogo`, `MIXXBanner`.

**Errors / side effects:** outer catch logs; email fail leaves request Pending; Redis unlock always; no FCM.

**Evidence:** `TZ-Tigo-SuperApp-MChangoReportScheduler/TZTigoSuperAppMChangoReportScheduler/Worker.cs › Worker.ExecuteAsync` @ `34ba77f`; `.../Services/BackgroundService/ReportSendingService.cs › SendReportToRecipient`.

## BE-JOB-MCHRPT-002 InterestCalculationService

**Trigger:** host start loads `mchangointerestconfiguration` (cutoff + `holidaycalculation`). Cron `{cutoffMin+1} {cutoffHour} * * *` or weekdays via NCrontab. Does **not** read appsettings `InterestCalculation:*`. Email keys `EmailTo`, `EmailCC`, `SmtpServer`, `SmtpPort`, `SmtpUsername`, `SmtpPassword`.

**Steps:**
1. `StartAsync` load config; abort if cutoff missing.
2. `DoWork` → `IntersetCalculation`.
3. R active Account; R TransactionHistory window (cutoff; Mon+!holiday → 3 days else 1).
4. Per account: deposits/withdrawals → interest math → W `AccountInterestCalculation`.
5. Totals → W `GrossInterestCalculation`.
6. Excel base64 → SMTP (email errors after DB writes).

**Data:** R `mchangointerestconfiguration` (`ConnectionStrings:TZConfigurationService`); R Account / TransactionHistory; W AccountInterestCalculation / GrossInterestCalculation.

**Downstream:** SMTP only. No MTPG/FCM.

**Evidence:** `TZ-Tigo-SuperApp-MChangoReportScheduler/TZTigoSuperAppMChangoReportScheduler/Services/BackgroundService/InterestCalculationService.cs › StartAsync` / `DoWork` / `IntersetCalculation` @ `34ba77f`.
