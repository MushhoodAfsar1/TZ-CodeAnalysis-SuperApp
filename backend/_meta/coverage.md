---
kb_section: backend
type: meta
ids: [BE-META-COV]
service: ALL
repo: multi
repo_ref: checked-out
repo_sha: multi
updated: 2026-10-05
confidence: confirmed
---

# Coverage

HTTP actions found = documented `apis/*.md` count (static `[Http*]` parse). Portal rows are Angular `HttpClient` calls, not ASP.NET actions.

| Code | Status | analyzed_sha | Actions found | Actions documented | Jobs |
|---|---|---|---:|---:|---:|
| IDENT | deep-analyzed | `e7397b0` | 34 | 34 | 0 |
| SESS | deep-analyzed | `6f24061` | 4 | 4 | 0 |
| ACCOUNT | deep-analyzed | `5c549d6` | 51 | 51 | 0 |
| WALLET | deep-analyzed | `27737b1` | 7 | 7 | 0 |
| SEND | deep-analyzed | `599771b` | 15 | 15 | 0 |
| AIRTIME | deep-analyzed | `7a52359` | 10 | 10 | 0 |
| EXTPAY | deep-analyzed | `51718e1` | 6 | 6 | 0 |
| MERCH | deep-analyzed | `2367767` | 46 | 46 | 0 |
| MERSET | deep-analyzed | `d638213` | 0 | 0 | 1 |
| LOAN | deep-analyzed | `759a471` | 24 | 24 | 0 |
| SAVING | deep-analyzed | `2ca8791` | 8 | 8 | 0 |
| GRPSAV | deep-analyzed | `ed4ac20` | 65 | 65 | 0 |
| MCHANGO | deep-analyzed | `7c288ab` | 64 | 64 | 0 |
| MCHRPT | deep-analyzed | `34ba77f` | 0 | 0 | 2 |
| INSUR | deep-analyzed | `38747da` | 13 | 13 | 0 |
| VCARD | deep-analyzed | `db358e6` | 9 | 9 | 0 |
| DSTV | deep-analyzed | `fd31aa1` | 7 | 7 | 0 |
| GSM | deep-analyzed | `13fe724` | 16 | 16 | 0 |
| SELFC | deep-analyzed | `a0aeca8` | 57 | 57 | 0 |
| REWARD | deep-analyzed | `b47cb93` | 22 | 22 | 0 |
| NOTIF | deep-analyzed | `b7c98ec` | 19 | 19 | 1 |
| NOTSCH | deep-analyzed | `72838eb` | 0 | 0 | 1 |
| AUDIT | deep-analyzed | `eb87819` | 1 | 1 | 0 |
| EXPENSE | deep-analyzed | `e821ac9` | 15 | 15 | 0 |
| GAMES | deep-analyzed | `10c8daa` | 8 | 8 | 0 |
| RESERV | deep-analyzed | `dfd072a` | 13 | 13 | 0 |
| STOCK | deep-analyzed | `10f0a62` | 18 | 18 | 0 |
| PORTAL | deep-analyzed | `bb69e15` | 0 ASP.NET / 420 Angular HttpClient | 420 | 0 |
| CONFIG | deep-analyzed | `9c00072` | 432 `[Http*]` in `*Controller.cs` | 432 | 0 |

### Coverage notes
- **CONFIG:** 432 `[HttpGet|Post|Put|Delete|Patch]` in `*Controller.cs`. 422 on classes named `*Controller` (including Banner Create/Update missed by the first parser because of `[HttpPost("…"), DisableRequestSizeLimit]` — now BE-API-CONFIG-431/432). 10 more on `ManageFirebase` and `TimeBasedIcon`. **BE-GAP-009 closed.**
- **PORTAL:** Angular admin UI; no ASP.NET controllers. Documented calls are `HttpClient` path suffixes using environment **key names** `authApiUrl`, `configurationApiUrl`, `notificationUrl`, `mchangoUrl` (hosts omitted).
- **MERSET / MCHRPT / NOTSCH:** no HTTP controllers; jobs documented in `jobs.md`.
- **SHA refresh 2026-10-05:** all 29 checkouts still match analyzed_sha (no `git fetch`; porcelain CLEAN). Deepen pass expanded money-path nested DTOs, handler checks, and downstream config keys.
- **MCHRPT jobs:** two real hosted jobs (`Worker`, `InterestCalculationService`). Former BE-JOB-MCHRPT-004 (`ApplicationServiceExtensions`) retired as a false positive; ID not reused. `ReportSendingService` is scoped work of Worker.
