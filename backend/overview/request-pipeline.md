---
kb_section: backend
type: overview
ids: [BE-OV-PIPE]
service: ALL
repo: multi
repo_ref: checked-out
repo_sha: multi
updated: 2026-10-05
confidence: confirmed
---

# Request pipeline

There is **no API-gateway repo** in this workspace. The mobile client calls each service’s Kestrel endpoints (hosts not recorded). Typical money-path service:

```mermaid
sequenceDiagram
  participant App as Mobile app
  participant Enc as EncryptionProviderFilter
  participant Sess as SessionValidationFilter
  participant Ctrl as Controller
  participant Svc as Service / repository
  participant Cfg as CONFIG CMM
  App->>Enc: POST {payload: AES-or-JSON}
  Enc->>Enc: Decrypt payload to TEntity
  Enc->>Sess: Items.modeldata
  Sess->>Sess: JWT X-User-Session + Redis/DB
  Sess->>Ctrl: action
  Ctrl->>Svc: handler
  Svc->>Cfg: response-code lookup
  Ctrl->>Enc: BaseResponse envelope
  Enc->>App: AES-encrypted whole response (if enabled)
```

## Envelope
- Request: `{ "payload": "<string>" }` (`RequestModel.payload`) except Identity portal JWTs, Session `auth`, MChango middleware-bound DTOs, and helper `enc`/`dec` endpoints.
- Success (after `ApiResponseHandler`): `success`, `responseCode`, `transactionStatus`, `appVersionInfo`, `responseData`.
- Failure: `success`, `responseCode`, `appVersionInfo`, `errorDescription`.
- HTTP: 200 if `responseCode=="200"` else 201 on success; 400 or 500 on failure.

## Middleware variants
| Pattern | Services | Order |
|---|---|---|
| A | Most feature services | Swagger → Https → UseAuthorization → MapControllers |
| B | Wallet, Reward, Notification, AuditLogs | Swagger → GlobalError → Cors → Https → UseAuthorization → MapControllers |
| C | GSM | Cors → Https → UseAuthorization → GlobalError → MapControllers |
| D | Identity, Session | Cors → (Https) → UseAuthentication → UseAuthorization → MapControllers |
| E | MChango | EncryptionMiddleware → Cors → UseAuthentication → UseAuthorization → MapControllers |
| F | CONFIG | GlobalError → Https → Cors → UseAuthorization (JWT registered; UseAuthentication missing) |

No `Startup.cs`. Auth on money-path APIs is **filter-based**, not `UseAuthentication`.
