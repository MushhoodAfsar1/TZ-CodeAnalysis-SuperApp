---
kb_section: fe-mobile
type: catalog
ids: [FE-META-LOG]
feature: ALL
fe_ref: main
fe_sha: 6328b7254
updated: 2026-10-05
confidence: confirmed
---
# Changelog

## 2026-10-05 — Dashboard balance, airtime top-up, and bill pay

- Contract-diffed API-0018, API-0034, API-0035, API-0037, API-0049, API-0257, API-0258, and API-0259 against backend `0c13cc4`. All eight are `contract-mismatch`.
- Wrote SCR-0013–0018 and FLW-0006–FLW-0007. Added BR-0013–BR-0019 and GAP-0119–GAP-0126.
- Match totals: path-only 267, contract-mismatch 15, matched 2, fe-only 83.
- Corrected API-0035 request keys (`asseType` / `resultUrl`; `SP99860` is a `spCode` value) and API-0259 (short code and operator name only on the others branch).

## 2026-10-05 — Session, auth, and money deep pass

- Pinned the backend KB to `main` @ `0c13cc4` (contract deepen). FE stays `6328b7254`.
- Folded the SESS refresh slice into `fe-mobile/` (SCR-0001, FLW-0001, BR-0001–BR-0007). The `mobile/` tree is not copied.
- Wrote screens and flows for splash, login, OTP, onboarding, self-registration, PIN, local send money, and agent cash-out.
- Contract-diffed API-0001, API-0002, API-0003, API-0004, API-0013, API-0014, API-0202 (`contract-mismatch`) and API-0039, API-0041 (`matched`).
- Match totals: path-only 275, contract-mismatch 7, matched 2, fe-only 83.
- Added GAP-0105–GAP-0118. OTP V2 stays fe-only.

## 2026-10-05 — API inventory
- Created `fe-mobile/` and recorded FE `main` @ `6328b7254`.
- Catalogued 367 live HTTP calls (`API-0001`–`API-0367`) with path-suffix backend match.
- Match counts: path-only 284, fe-only 83.
- Opened 104 gaps (per fe-only call, plus one be-only rollup per touched service, plus Group Saving duplicate paths).
- Screen inventory and per-feature deep passes are not started.
