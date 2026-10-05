---
kb_section: mobile
type: catalog
ids: [FE-CAT-MATCH]
service: ALL
repo: TZ-Tigo-SuperApp-Mobile
repo_ref: main
repo_sha: 6328b7254
be_kb_ref: cursor/frontend-mobile-api-analysis-ad82
be_kb_sha: 2655b7a
updated: 2026-10-05
confidence: confirmed
---

# API match (master join)

One row per backend API **after that service is analyzed**. Unprocessed services stay in [`../_meta/coverage.md`](../_meta/coverage.md) and are not listed here yet.

Resolved paths omit the host. The gateway prefix (`sessions`, `accounts`, …) is the segment the app concatenates in front of `/api/...`.

| BE ID | Method + public_path | Class | Match status | FE method (`ApiManager.x`) | FE endpoint const | Use-case | Enc. | Callers (FE-SCR) | FE file | Searched (if not-in-fe) | Conf. |
|---|---|---|---|---|---|---|---|---|---|---|---|
| BE-API-SESS-001 | POST `/api/Account/auth` | mobile-candidate | not-in-fe | — | — | — | — | — | — | `Account/auth`, `sessions/api` under `lib/` (only `sessions/api/Account/refreshToken` exists) | confirmed |
| BE-API-SESS-002 | POST `/api/Account/refreshToken` | mobile-candidate | fe-used | `ApiManager.requestRefreshLoginAuthToken` (wrapper `ApiManager.callRefreshLoginAuthToken`) | `UrlConstants.requestRefreshLoginAuthToken` → `sessions/api/Account/refreshToken` | none | yes, `payload` AES | FE-SCR-001; app shell; any call that returns HTTP 410 | [`../services/sess/apis/accountcontroller-refresh-002.md`](../services/sess/apis/accountcontroller-refresh-002.md) | — | confirmed |
| BE-API-SESS-003 | POST `/api/Account/enc` | helper | n/a-helper | — | — | — | — | — | — | `Account/enc`, `enc_payment` under the FE repo | confirmed |
| BE-API-SESS-004 | POST `/api/Account/decreq` | helper | n/a-helper | — | — | — | — | — | — | `decreq`, `dec_req` under the FE repo | confirmed |
