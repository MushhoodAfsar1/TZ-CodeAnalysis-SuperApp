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

How other agents should use this folder. Source of truth for behaviour is the tigopesa Flutter app at `main` @ `6328b7254` (`6328b7254cdae4468d124da79011cc6b30ec2087`). Backend contracts live in `backend/` and are not edited from here.

## Start here
1. [`catalog/api-catalog.md`](catalog/api-catalog.md) — every live FE HTTP call (`API-####`), path, encryption, request field names, file-level callers, backend path match.
2. [`gaps/fe-be-gaps.md`](gaps/fe-be-gaps.md) and [`gaps/unmapped.md`](gaps/unmapped.md) — paths the two catalogs do not share.
3. [`_meta/coverage.md`](_meta/coverage.md) — which features are not started. Screen and flow files are not written yet.
4. [`overview/architecture.md`](overview/architecture.md) — where calls are built.

## IDs
`API-` live FE call · `SCR-` screen (none assigned yet) · `FLW-` flow · `BR-` business rule · `INT-` integration · `GAP-` mismatch.

## Match status
`path-only` = `/api/...` suffix matches a `BE-API-*` row; body not compared. `fe-only` = no backend row. `matched` is reserved for a later contract diff. Do not treat `path-only` as a verified contract.

## Not in this pass
Screens, navigation guards, response fields the UI reads, and business rules. See `_meta/coverage.md` for the resume point.
