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
| `SCR-####` | Screen, bottom sheet, or dialog that drives logic | Not assigned yet |
| `FLW-####` | Multi-screen flow | Not assigned yet |
| `BR-####` | Rule the app enforces or assumes | Not assigned yet |
| `INT-####` | SDK or platform capability | Assigned from pubspec presence |
| `GAP-####` | FE/BE mismatch | One row per fe-only API; be-only grouped by service |

Backend IDs stay as published: `BE-API-<SERVICE>-###`.

## Confidence
- **confirmed** — traced in code at the recorded SHA.
- **inferred** — naming or pubspec only.
- **partial** — some branches or layers untraced. The file says which.

## Match
`matched` · `path-only` · `contract-mismatch` · `fe-only` · `be-only` · `unknown`.

## Redaction
Field names, types, and sources only. No keys, tokens, real phone numbers, balances, or hostnames.
