---
kb_section: mobile
type: meta
ids: [FE-META-CONV]
service: ALL
repo: TZ-Tigo-SuperApp-Mobile
repo_ref: main
repo_sha: 6328b7254
be_kb_ref: cursor/frontend-mobile-api-analysis-ad82
be_kb_sha: 2655b7a
updated: 2026-10-05
confidence: confirmed
---

# Conventions

Same style as `backend/_meta/conventions.md`. Mobile IDs use the backend number when they describe the same API.

| Pattern | Meaning |
|---|---|
| `FE-API-<CODE>-###` | Mobile usage of `BE-API-<CODE>-###`. Same number. |
| `FE-API-X-###` | Mobile call with no backend match (reverse sweep). |
| `FE-SCR-###` | Screen, bottom sheet, or dialog that calls an API or enforces a rule. |
| `FE-FLW-###` | User journey. Links `BE-FLW-###` when one exists. |
| `FE-BR-<CODE>-###` | Rule the app enforces or assumes around that service. `APP` is app-wide. |
| `FE-INT-###` | SDK or platform integration. |
| `FE-GAP-###` | Mobile ↔ backend mismatch. |

## Match status

| Status | Meaning |
|---|---|
| `fe-used` | A mobile method exists and at least one call site can run. |
| `fe-defined-unused` | Method or constant exists, no call site. |
| `not-in-fe` | Searched, no hit. |
| `ambiguous` | More than one candidate, or the path is built dynamically. |
| `n/a-non-mobile` | Admin or back-office, and a quick search found no app call. |
| `n/a-helper` | Crypto test endpoint, and a quick search found no app call. |

## Confidence

- **confirmed**: traced end to end at the recorded FE SHA.
- **partial**: call site confirmed; some branches not traced.
- **inferred**: naming or a dynamic path only.

## Redaction

Document field name, type, source, and constraint. Do not copy keys, tokens, MSISDNs, hosts, or other secrets. Samples use the backend placeholders.
