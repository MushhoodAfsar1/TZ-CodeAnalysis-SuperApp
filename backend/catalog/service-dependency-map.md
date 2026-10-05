---
kb_section: backend
type: catalog
ids: [BE-CAT-DEP]
service: ALL
repo: multi
repo_ref: checked-out
repo_sha: multi
updated: 2026-10-05
confidence: confirmed
---

# Service dependency map

```mermaid
flowchart TD
  ACCOUNT -->|SMM auth| SESS
  ACCOUNT -->|CMM| CONFIG
  WALLET -->|CMM| CONFIG
  SEND -->|CMM| CONFIG
  AIRTIME -->|CMM| CONFIG
  EXTPAY -->|CMM| CONFIG
  MERCH -->|CMM| CONFIG
  MERSET -->|schedules| MERCH
  LOAN -->|CMM| CONFIG
  SAVING -->|CMM| CONFIG
  GRPSAV -->|CMM| CONFIG
  MCHANGO -->|CMM| CONFIG
  MCHRPT --> MCHANGO
  NOTSCH --> NOTIF
  CONFIG -->|IdentityApi| IDENT
  PORTAL --> IDENT
  PORTAL --> CONFIG
```
