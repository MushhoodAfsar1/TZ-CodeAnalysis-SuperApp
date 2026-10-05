---
kb_section: mobile
type: catalog
ids: [FE-CAT-MATRIX]
service: ALL
repo: TZ-Tigo-SuperApp-Mobile
repo_ref: main
repo_sha: 6328b7254
be_kb_ref: cursor/frontend-mobile-api-analysis-ad82
be_kb_sha: 2655b7a
updated: 2026-10-05
confidence: confirmed
---

# Screen × API matrix

| Screen | BE-API | Trigger | Condition(s) | Order | Fg/Bg | On success | On failure | Rules | Conf. |
|---|---|---|---|---|---|---|---|---|---|
| FE-SCR-001 Merchant home | BE-API-SESS-002 Refresh | App resume (`onResumed`) | User is logged in, then the refresh window in FE-BR-SESS-001 | 1 | Bg | New access and refresh tokens stored; `loggedInTime` set to now | Stays on the screen. Call counter resets. No message. | FE-BR-SESS-001, FE-BR-SESS-002, FE-BR-SESS-003, FE-BR-SESS-006 | confirmed |
| App shell (`main.dart` Listener) | BE-API-SESS-002 Refresh | Pointer down, move, or up | Same as the home row | 1 | Bg | Same as the home row | Same as the home row | FE-BR-SESS-001, FE-BR-SESS-002, FE-BR-SESS-003, FE-BR-SESS-006 | confirmed |
| Any in-flight API (`NetworkManager.callDioAPI`) | BE-API-SESS-002 Refresh | HTTP 410 on that call | Fewer than 3 refresh attempts already counted for this call chain | before retry of the original call | Bg | Original call is sent again with the new `X-User-Session` | Original call completes as a network failure (callback `success` false). No session-expired dialog. | FE-BR-SESS-004, FE-BR-SESS-005 | confirmed |
