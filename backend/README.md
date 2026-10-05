---
kb_section: backend
type: overview
ids: [BE-README]
service: ALL
repo: TZ-CodeAnalysis-SuperApp
repo_ref: analysis/be/full-20261005
repo_sha: pending
updated: 2026-10-05
confidence: confirmed
---

# TZ SuperApp backend knowledge base

Static analysis of the 29 `TZ-Tigo-SuperApp-*` checkouts. **Contracts are decrypted DTO shapes**, not ciphertext.

## How to use
1. FE/match: [`catalog/api-catalog.md`](catalog/api-catalog.md)
2. Pipeline/crypto/errors: [`overview/`](overview/)
3. Per service: [`services/<code>/`](services/) — one file per HTTP action under `apis/`
4. Cross-service: [`flows/`](flows/)
5. Gaps: [`gaps/be-internal-gaps.md`](gaps/be-internal-gaps.md)

## Legend
IDs: `BE-API-*` actions · `BE-BR-*` rules · `BE-ERR-*` errors · `BE-JOB-*` jobs · `BE-FLW-*` flows · `BE-GAP-*` gaps.

Confidence: confirmed (code at SHA) · partial (route/DTO ok, handler branches incomplete) · inferred.

## Index
See [`_meta/coverage.md`](_meta/coverage.md) and [`_meta/repo-registry.md`](_meta/repo-registry.md).
