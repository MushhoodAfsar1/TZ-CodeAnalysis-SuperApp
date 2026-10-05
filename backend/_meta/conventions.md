---
kb_section: backend
type: meta
ids: [BE-META-CONV]
service: ALL
repo: TZ-CodeAnalysis-SuperApp
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: n/a
updated: 2026-10-05
confidence: confirmed
---
# Conventions

## IDs
`BE-SVC-<CODE>` · `BE-API-<CODE>-###` · `BE-BR-<CODE>-###` · `BE-ERR-<CODE>-###` · `BE-EVT-<CODE>-###` · `BE-JOB-<CODE>-###` · `BE-INT-<CODE>-###` · `BE-FLW-###` · `BE-GAP-###`

IDs are stable and never reused.

## Status
`not-started` → `discovered` → `inventoried` → `deep-analyzed` → `flows-linked` → `verified` · `stale`

## Confidence
`confirmed` (traced in code at SHA) · `inferred` (say why) · `partial` (list untraced branches)

## Redaction
Document decrypted **shape**, never secrets, tokens, real MSISDNs, PINs, keys, connection strings, or hosts.

## Match keys
`public_method`, `public_path`, `internal_path`, `dispatch_field`, `dispatch_value`, `controller_action`, `topic`
