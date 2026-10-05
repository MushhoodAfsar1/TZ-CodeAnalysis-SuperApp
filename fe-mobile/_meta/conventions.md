---
kb_section: fe-mobile
type: catalog
ids: [FE-META-CONV]
feature: ALL
fe_ref: main
fe_sha: 6328b7254
updated: 2026-10-05
confidence: confirmed
---
# Conventions

## IDs
| Prefix | Meaning | Rule |
|---|---|---|
| `API-####` | One live `callDioAPI` (a method with two endpoints gets two IDs) | Never reuse or renumber |
| `SCR-####` | Screen, bottom sheet, or dialog that drives logic | Next free `SCR-0019` |
| `FLW-####` | Multi-screen flow | Next free `FLW-0008` |
| `BR-####` | Rule the app enforces or assumes | Next free `BR-0020` |
| `INT-####` | SDK or platform capability | Assigned from pubspec presence |
| `GAP-####` | FE/BE mismatch | Next free `GAP-0127`. One row per fe-only API; be-only grouped by service; contract diffs add their own rows |

Backend IDs stay as published: `BE-API-<SERVICE>-###`.

## Confidence
- **confirmed** — traced in code at the recorded SHA.
- **inferred** — naming or pubspec only.
- **partial** — some branches or layers untraced. The file says which.

## Match
`matched` · `path-only` · `contract-mismatch` · `fe-only` · `be-only` · `unknown`.

`matched` and `contract-mismatch` require a written diff (see `contracts/`). A path hit alone stays `path-only`.

## Redaction
Field names, types, and sources only. No keys, tokens, real phone numbers, balances, or hostnames.
