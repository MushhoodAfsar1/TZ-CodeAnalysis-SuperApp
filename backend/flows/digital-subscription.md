---
kb_section: backend
type: flow
ids: [BE-FLW-012]
service: ALL
repo: multi
repo_ref: checked-out
repo_sha: multi
updated: 2026-10-05
confidence: partial
---

# BE-FLW-012 Digital subscription

**Hops (sync unless noted):** DSTV controller

```mermaid
sequenceDiagram
  participant App
  participant Svc as Feature service
  participant Cfg as CONFIG
  participant Sess as SESS/local JWT filter
  App->>Sess: X-User-Session
  App->>Svc: encrypted payload
  Svc->>Cfg: response codes / catalogues
  Svc->>App: envelope
```

Failure: session 410; handler 400/500; CONFIG lookup failure falls back to handler messages. No distributed saga/compensation parsed; money movement is downstream MMP HTTP with local response mapping.

See `catalog/api-catalog.md` for match keys. Evidence: per-service controllers at recorded SHAs.
