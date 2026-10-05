---
kb_section: backend
type: service
ids: [BE-SVC-MCHRPT]
service: MCHRPT
repo: TZ-Tigo-SuperApp-MChangoReportScheduler
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 34ba77f
updated: 2026-10-05
confidence: partial
---

# Jobs — MCHRPT

| ID | Kind | Class | File | Notes |
|---|---|---|---|---|
| BE-JOB-MCHRPT-001 | BackgroundService | `Worker` | `TZTigoSuperAppMChangoReportScheduler/Worker.cs` |  |
| BE-JOB-MCHRPT-002 | BackgroundService | `ReportSendingService` | `TZTigoSuperAppMChangoReportScheduler/Services/BackgroundService/ReportSendingService.cs` |  |
| BE-JOB-MCHRPT-003 | IHostedService | `InterestCalculationService` | `TZTigoSuperAppMChangoReportScheduler/Services/BackgroundService/InterestCalculationService.cs` |  |
| BE-JOB-MCHRPT-004 | *(not a job)* | `ApplicationServiceExtensions` | `.../Common/Extensions/ApplicationServiceExtensions.cs` | DI registrar; counted because file text contains `BackgroundService`. |

## BE-JOB-MCHRPT-001 / 002 Report sending
**Trigger:** `Worker` hosted loop calling `IReportSendingService` / `ReportSendingService`.
**Purpose:** send MChango reports (email/outbox — see class).
**Evidence:** `TZ-Tigo-SuperApp-MChangoReportScheduler/TZTigoSuperAppMChangoReportScheduler/Worker.cs`.

## BE-JOB-MCHRPT-003 InterestCalculationService
**Trigger:** `IHostedService` (runs interest calculation; MChango copies of this hosted service are commented out).
**Evidence:** `.../Services/BackgroundService/InterestCalculationService.cs` @ `34ba77f`.
