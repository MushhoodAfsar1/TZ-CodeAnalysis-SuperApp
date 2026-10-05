---
kb_section: mobile
type: meta
ids: [FE-META-COV]
service: ALL
repo: TZ-Tigo-SuperApp-Mobile
repo_ref: main
repo_sha: 6328b7254
be_kb_ref: cursor/frontend-mobile-api-analysis-ad82
be_kb_sha: 2655b7a
updated: 2026-10-05
confidence: confirmed
---

# Coverage

BE API counts come from `backend/_meta/coverage.md`. Match columns are filled when that service is analyzed. Schedulers with no HTTP actions are `n/a` (nothing for the app to call).

| Code | BE APIs | mobile-candidate | fe-used | fe-defined-unused | not-in-fe | ambiguous | n/a | Status | fe_sha | be_kb_sha | Date |
|---|---:|---:|---:|---:|---:|---:|---:|---|---|---|---|
| SESS | 4 | 2 | 1 | 0 | 1 | 0 | 2 | deep-analyzed | 6328b7254 | 2655b7a | 2026-10-05 |
| ACCOUNT | 51 | | | | | | | queued | | | |
| WALLET | 7 | | | | | | | queued | | | |
| SEND | 15 | | | | | | | queued | | | |
| AIRTIME | 10 | | | | | | | queued | | | |
| EXTPAY | 6 | | | | | | | queued | | | |
| MERCH | 46 | | | | | | | queued | | | |
| MERSET | 0 | 0 | 0 | 0 | 0 | 0 | 0 | n/a | | | 2026-10-05 |
| LOAN | 24 | | | | | | | queued | | | |
| SAVING | 8 | | | | | | | queued | | | |
| GRPSAV | 65 | | | | | | | queued | | | |
| MCHANGO | 64 | | | | | | | queued | | | |
| MCHRPT | 0 | 0 | 0 | 0 | 0 | 0 | 0 | n/a | | | 2026-10-05 |
| INSUR | 13 | | | | | | | queued | | | |
| VCARD | 9 | | | | | | | queued | | | |
| DSTV | 7 | | | | | | | queued | | | |
| GSM | 16 | | | | | | | queued | | | |
| SELFC | 57 | | | | | | | queued | | | |
| REWARD | 22 | | | | | | | queued | | | |
| NOTIF | 19 | | | | | | | queued | | | |
| NOTSCH | 0 | 0 | 0 | 0 | 0 | 0 | 0 | n/a | | | 2026-10-05 |
| EXPENSE | 15 | | | | | | | queued | | | |
| GAMES | 8 | | | | | | | queued | | | |
| RESERV | 13 | | | | | | | queued | | | |
| STOCK | 18 | | | | | | | queued | | | |
| CONFIG | 430 | | | | | | | queued | | | |
| IDENT | 34 | | | | | | | queued | | | |
| AUDIT | 1 | | | | | | | queued | | | |
| PORTAL | 420 | | | | | | | queued | | | |

### Notes

- **SESS:** `BE-API-SESS-002` is `fe-used`. `BE-API-SESS-001` is `not-in-fe`. `BE-API-SESS-003` and `BE-API-SESS-004` are `n/a-helper`.
- **MERSET / MCHRPT / NOTSCH:** no HTTP actions in the backend knowledge base. No mobile search.
- **Phase 1** (full `ApiManager` index) is not done. SESS was matched by path search.
