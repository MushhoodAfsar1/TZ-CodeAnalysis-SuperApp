---
kb_section: backend
type: gap
ids: [BE-GAP-000]
service: ALL
repo: multi
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: multi
updated: 2026-10-05
confidence: confirmed
---
# BE internal gaps

| ID | Type | Description | Evidence | Impact | Severity | Suggested owner | Status |
|---|---|---|---|---|---|---|---|
| BE-GAP-001 | unknown-dispatch | No API gateway repo in the environment; public paths may differ from controller routes | repo set | FE matching | high | platform | open |
| BE-GAP-002 | inconsistent-error-model | IDENT uses BaseDto; SESS refresh uses HTTP 411; session filter uses HTTP 410 | overview/error-model.md | client handling | medium | BE | open |
| BE-GAP-003 | undocumented-behaviour | IDENT EncryptionProviderFilter exists but AccountController actions bind plaintext DTOs (filter not applied on those actions) | Identity AccountController vs Filter | crypto coverage | medium | IDENT | open |
| BE-GAP-004 | undocumented-behaviour | CONFIG: 432 Http* attributes vs 419 parsed actions (13 non-standard signatures) | TZ-Tigo-SuperApp-Configuration controllers | incomplete CONFIG contracts | medium | CONFIG | open |
