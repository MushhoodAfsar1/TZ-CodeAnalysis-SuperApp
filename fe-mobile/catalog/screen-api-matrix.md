---
kb_section: fe-mobile
type: catalog
ids: [FE-CAT-MATRIX]
feature: ALL
fe_ref: main
fe_sha: 6328b7254
be_kb_sha: 0c13cc4
updated: 2026-10-05
confidence: partial
---
# Screen → API matrix

Rows below are the traced session/auth and money triggers. Other API IDs stay in [`api-catalog.md`](api-catalog.md) without a screen yet.

| Screen | API | Trigger | Condition(s) | Order | Fg/Bg | On success | On failure | BE | Conf. |
|---|---|---|---|---|---|---|---|---|---|
| SCR-0002 | API-0367 | Splash start | Gateway token missing or expired | 1 | Fg | Store gateway token, continue | Stay / retry path in controller | — fe-only | confirmed |
| SCR-0002 | API-0007 | After remote config | Pre-login cache or version miss | 2 | Fg | Save guest and more flags | No-internet still redirects | BE-API-CONFIG-401 path-only | confirmed |
| SCR-0002 | API-0318 | Redirect | After the checks above | 3 | Fg | `AppUtil.boResponse` | Error handling in controller | BE-API-CONFIG-392 path-only | partial |
| SCR-0005 | API-0004 | Next on phone | MSISDN length ≥ 9 and prefix valid | 1 | Fg | Branch on `UM-Lo-*` | Generic error | BE-API-ACCOUNT-011 contract-mismatch | confirmed |
| SCR-0004 | API-0005 | `onReady` and resend | Timer done on resend; not already in progress | 1 | Fg | Start entry; read `isDebugNumber` | Error dialog | fe-only | confirmed |
| SCR-0004 | API-0006 | Code complete | Length is the platform max | 2 | Fg | Login, permission, or back | Stay on OTP | fe-only | confirmed |
| SCR-0003 | API-0001 | Login tap or biometrics | PIN length 4 | 1 | Fg | Store `accessCode`, open shell | `UM-Lo-01` to OTP, else clear PIN | BE-API-ACCOUNT-002 contract-mismatch | confirmed |
| SCR-0001 | API-0003 | `onResumed` | Logged in and BR-0001 window | 1 | Bg | Replace tokens | Stay, or login if refresh expiry passed | BE-API-SESS-002 contract-mismatch | confirmed |
| App shell | API-0003 | Pointer down/move/up | Same window | 1 | Bg | Replace tokens | Same | BE-API-SESS-002 contract-mismatch | confirmed |
| Any in-flight call | API-0003 | HTTP 410 | Retry count ≤ 2 | before retry | Bg | Retry original POST | Original call fails | BE-API-SESS-002 contract-mismatch | confirmed |
| SCR-0006 | API-0198 | NIDA submit | Form filled | 1 | Fg | Compare `idValue`, open SCR-0007 | Error | BE-API-ACCOUNT-012 path-only | partial |
| SCR-0007 | API-0200 | OTP sheet | After NIDA questions | 1 | Fg | Enter code | Error | fe-only | partial |
| SCR-0007 | API-0201 | Code entered | Self-onboard OTP | 2 | Fg | API-0202 | Stay | fe-only | partial |
| SCR-0007 | API-0202 | OTP ok | — | 3 | Fg | Open SCR-0008 | Error | BE-API-ACCOUNT-014 contract-mismatch | partial |
| SCR-0008 | API-0073 | New PIN matches | Length 4 | 1 | Fg | Done / login | Error | BE-API-SELFC-010 path-only | confirmed |
| SCR-0008 | API-0075 | Reset NIDA submit | NIDA length check | 1 | Fg | SCR-0004 | Error | BE-API-SELFC-009 path-only | partial |
| SCR-0009 | API-0013 | Next | Amount in range and wallet selected | 2 (after contact verify) | Fg | SCR-0010 with fees | Error | BE-API-SEND-010 contract-mismatch | partial |
| SCR-0010 | API-0014 | Confirm | PIN length 4 | 1 | Fg | Receipt `transId` | Error | BE-API-SEND-011 contract-mismatch | partial |
| SCR-0011 | API-0039 | Next, consumer | Amount in cash-out range | 1 | Fg | SCR-0012 | Error | BE-API-WALLET-001 matched | confirmed |
| SCR-0012 | API-0041 | Confirm, consumer | PIN complete | 1 | Fg | Older receipt | Overdraft retry or error | BE-API-WALLET-002 matched | confirmed |
