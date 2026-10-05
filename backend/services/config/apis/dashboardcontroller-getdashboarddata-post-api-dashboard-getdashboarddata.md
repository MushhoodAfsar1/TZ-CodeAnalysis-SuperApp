---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-362]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-362 DashboardController.GetDashboardData
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/DashboardController.cs › DashboardController.GetDashboardData` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/dashboard/GetDashboardData
  internal_path: /api/dashboard/GetDashboardData
  dispatch_field: null
  dispatch_value: null
  controller_action: DashboardController.GetDashboardData
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** DashboardRequest

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| msisdn | `string` | no | — | DataAnnotations / action | — |
| country | `string?` | no | — | DataAnnotations / action | — |
| sections | `string?` | no | — | DataAnnotations / action | — |
| isrevamp | `bool` | no | — | DataAnnotations / action | — |
| role | `string?` | no | — | DataAnnotations / action | — |
| groupType | `int?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "msisdn": "<msisdn>", "country": "<country>", "sections": "<sections>", "isrevamp": "<isrevamp>", "role": "<role>", "groupType": "<groupType>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Guard: Data returned successfully | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/AppController/DashboardController.cs › DashboardController.GetDashboardData` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `DashboardController.GetDashboardData`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/AppController/DashboardController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as DashboardController
  participant Svc as downstream
  App->>Ctrl: POST /api/dashboard/GetDashboardData
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
| — | 200-envelope | — | success=false envelope | Data returned successfully | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/config/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/DashboardController.cs › DashboardController.GetDashboardData` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
