---
kb_section: mobile
type: overview
ids: [FE-README]
service: ALL
repo: TZ-Tigo-SuperApp-Mobile
repo_ref: main
repo_sha: 6328b7254
be_kb_ref: cursor/frontend-mobile-api-analysis-ad82
be_kb_sha: 2655b7a
updated: 2026-10-05
confidence: confirmed
---

# TZ SuperApp mobile knowledge base

How the Flutter app (`TZ-Tigo-SuperApp-Mobile`) uses the backend documented in [`backend/`](../backend/README.md).

Join a backend contract to its mobile usage by path substitution `backend/` ↔ `mobile/` and the same ID number: `BE-API-SESS-002` ↔ `FE-API-SESS-002`.

## Pins

| Side | Ref | SHA |
|---|---|---|
| FE app | `main` | `6328b7254` |
| BE knowledge base | `cursor/frontend-mobile-api-analysis-ad82` (README `repo_ref`: `analysis/be/full-20261005`) | `2655b7a` |

## How to use

1. Start at [`catalog/api-match.md`](catalog/api-match.md) for a backend API the app calls.
2. Open the matching file under [`services/<code>/apis/`](services/).
3. Screens that drive those calls are in [`catalog/screen-catalog.md`](catalog/screen-catalog.md) and [`catalog/screen-api-matrix.md`](catalog/screen-api-matrix.md).
4. Rules: [`catalog/business-rules.md`](catalog/business-rules.md). Gaps: [`gaps/fe-be-gaps.md`](gaps/fe-be-gaps.md).
5. What is done: [`_meta/coverage.md`](_meta/coverage.md).

A backend API the app does not call has a row in the match catalog and in coverage. It does not get a file under `services/`.

## Legend

IDs and confidence: [`_meta/conventions.md`](_meta/conventions.md).

Field samples use the same placeholders as the backend knowledge base (`255XXXXXXXXX`, `<jwt>`, `<device-id>`). Hosts, keys, and personal data are not copied here.
