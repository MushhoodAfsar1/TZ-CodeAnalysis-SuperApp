---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-308]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-308 InternationalUserRequestController.GetById
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/InternationalUserRequestController.cs › InternationalUserRequestController.GetById` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: GET
  public_path: /api/InternationalUserRequest/GetById/{id}
  internal_path: /api/InternationalUserRequest/GetById/{id}
  dispatch_field: null
  dispatch_value: null
  controller_action: InternationalUserRequestController.GetById
  topic: null
```

## Exposure & security
- **Auth:** JWT
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| id | `int` | yes | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "id": "<id>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | JWT via `X-User-Session` / Bearer | 401 | — | `TZTigoSuperAppConfiguration/Controllers/BO/InternationalUserRequestController.cs › InternationalUserRequestController` |
| 2 | Guard: success = false, responseCode = "404", responseMessage_en = "Request not found.", responseMessage_fr = "Ombi halijapatikana.", Data = null  | HTTP 404 | — | `TZTigoSuperAppConfiguration/Controllers/BO/InternationalUserRequestController.cs › InternationalUserRequestController.GetById` |
| 3 | Guard: Request not found. | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/InternationalUserRequestController.cs › InternationalUserRequestController.GetById` |
| 4 | Guard: Data retrieved successfully. | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/InternationalUserRequestController.cs › InternationalUserRequestController.GetById` |
| 5 | Guard: Failed to retrieve data. | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/InternationalUserRequestController.cs › InternationalUserRequestController.GetById` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `InternationalUserRequestController.GetById`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/BO/InternationalUserRequestController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as InternationalUserRequestController
  participant Svc as downstream
  App->>Ctrl: GET /api/InternationalUserRequest/GetById/{id}
  Ctrl->>Svc: business calls
  Svc-->>Ctrl: result
  Ctrl-->>App: envelope
```

## Downstream
| Order | Target (BE-API / BE-INT / BE-EVT) | Sync/Async | Condition | Sent / used fields |
|---|---|---|---|---|
| 1 | In-process services / EF / cache | Sync | always | see call chain |

## Data touched
| Entity / table / SP | R/W | Notes |
|---|---|---|
| See service data-model | R/W | Traced at SHA 9c00072 |

## Response (decrypted)
| Field (JSON) | Type | Always / when | Meaning |
|---|---|---|---|
| success | bool | typical | Operation flag |
| responseCode / responseMessage_* | string | typical | Envelope |
| Data / responseData | object | on success | Payload |

Sample (synthetic):
```json
{ "success": true, "responseCode": "00", "Data": {} }
```

## Errors
| BE code | HTTP | ID | Condition | Message key/text | Retryable |
|---|---|---|---|---|---|
| — | 404 | — | reachable return | success = false, responseCode = "404", responseMessage_en = "Request not found.", responseMessage_fr = "Ombi halijapatikana.", Data = null  | no |
| — | 200-envelope | — | success=false envelope | Request not found. | no |
| — | 200-envelope | — | success=false envelope | Data retrieved successfully. | no |
| — | 200-envelope | — | success=false envelope | Failed to retrieve data. | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/config/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/InternationalUserRequestController.cs › InternationalUserRequestController.GetById` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
