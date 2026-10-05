---
kb_section: backend
type: overview
ids: [BE-OVR-ARCH]
service: ALL
repo: multi
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: multi
updated: 2026-10-05
confidence: confirmed
---
# System architecture

29 repositories: ASP.NET Core `net8.0` microservices plus an Angular admin portal. There is **no API gateway repo** in this environment. The mobile app likely calls each service (or an undocumented gateway) with:

```mermaid
flowchart LR
  App[Mobile app] --> Enc[AES envelope payload]
  Enc --> Svc[Feature service]
  Svc --> SessVal[SessionValidationFilter]
  SessVal --> Redis[(Redis device_session)]
  SessVal --> Tokens[(tokens table)]
  Svc --> Ident[IDENT portal JWT]
  Svc --> Ext[External SOAP/HTTP]
  Svc --> MQ[RabbitMQ / MassTransit]
  Portal[Angular WebPortal] --> IDENT
  Portal --> CONFIG
```

Feature services share a copied pattern: `RequestModel.payload` + `EncryptionProviderFilter<T>` + `SessionValidationFilter` + `X-User-Session`. IDENT is different: ASP.NET Identity + LDAP for the **web portal**, JWT in `X-User-Session`. SESS issues mobile JWTs keyed by `msisdn` + `deviceid`.
