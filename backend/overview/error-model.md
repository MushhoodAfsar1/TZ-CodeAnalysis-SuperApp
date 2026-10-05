---
kb_section: backend
type: overview
ids: [BE-OVR-ERR]
service: ALL
repo: multi
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: multi
updated: 2026-10-05
confidence: confirmed
---
# Error model

There is **no single shared error library**. Patterns:

| Surface | Shape | Notes |
|---|---|---|
| IDENT | `BaseDto<T>` `{ success, responseCode, responseMessage_en, responseMessage_fr, Data }` | Also raw `BadRequest(string)` / 500 string |
| SESS refresh | anonymous object `{ success, responseCode, errordescription, responseData }` | Invalid token → HTTP 411 |
| Mobile features | `{ success, responseCode, errordescription, responseData }` or service-specific | Session filter uses HTTP 410 |
| Encryption on 401 | IDENT filter maps 401 → 411 when encrypting | `EncryptionProviderFilter` |

Treat Swagger comments as inferred. Codes like `RG-UP-01` appear in SESS refresh failure.
