---
kb_section: backend
type: catalog
ids: [BE-CAT-DEP]
service: ALL
repo: multi
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: multi
updated: 2026-10-05
confidence: confirmed
---
# Service dependency map

```mermaid
flowchart TB
  IDENT --> LDAP[LDAP AD]
  IDENT --> OTP[Email/SMS OTP]
  SESS --> ACCOUNT
  SESS --> Redis
  Feature[Feature services] --> SESS
  Feature --> ACCOUNT
  Feature --> CONFIG
  Feature --> AUDIT
  Feature --> NOTIF
```
