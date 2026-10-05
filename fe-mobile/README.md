---
kb_section: fe-mobile
type: overview
ids: [FE-README]
feature: ALL
fe_ref: main
fe_sha: 6328b7254
updated: 2026-10-05
confidence: partial
---
# Frontend mobile knowledge base

How other agents should use this folder. Source of truth for behaviour is the tigopesa Flutter app at `main` @ `6328b7254` (`6328b7254cdae4468d124da79011cc6b30ec2087`). Backend contracts live in `backend/` on analysis `main` @ `0c13cc4` and are not edited from here.

## Start here
1. [`catalog/api-catalog.md`](catalog/api-catalog.md) — every live FE HTTP call (`API-####`), path, encryption, request field names, file-level callers, backend match.
2. [`contracts/session-auth-money.md`](contracts/session-auth-money.md) — field diffs for login, refresh, CheckAuth, OTP, register, send money, and consumer cash-out. [`contracts/dashboard-airtime-bills.md`](contracts/dashboard-airtime-bills.md) — balance, airtime top-up, and bill pay.
3. [`catalog/screen-catalog.md`](catalog/screen-catalog.md) and [`flows/`](flows/) — session/auth, local send money, cash-out, dashboard balance, airtime top-up, and bill pay. Other features are not started.
4. [`gaps/fe-be-gaps.md`](gaps/fe-be-gaps.md) and [`gaps/unmapped.md`](gaps/unmapped.md) — paths the two catalogs do not share, plus contract gaps GAP-0105–GAP-0126.
5. [`_meta/coverage.md`](_meta/coverage.md) — which features are done.
6. [`overview/architecture.md`](overview/architecture.md) — where calls are built.

## IDs
`API-` live FE call · `SCR-` screen (through SCR-0018) · `FLW-` flow · `BR-` business rule · `INT-` integration · `GAP-` mismatch.

## Match status
`path-only` = `/api/...` suffix matches a `BE-API-*` row; body not compared. `fe-only` = no backend row. `matched` = required decrypted fields line up with the deepened contract. `contract-mismatch` = a written field diff found a conflict. Do not treat `path-only` as a verified contract.

## Not in this pass
Dashboard menus and banners, airtime bundles, loans, savings, and the rest of `_meta/coverage.md`. Gift, international transfer, and ATM cash-out are named and not traced. Bank-transfer and DStv callers of the bill APIs were not re-walked.
