---
kb_section: backend
type: api-contract
ids: [BE-API-AUDIT-001]
service: AUDIT
repo: TZ-Tigo-SuperApp-AuditLogs
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: eb87819
updated: 2026-10-05
confidence: confirmed
---
# BE-API-AUDIT-001 LogsController.CreateLogsAsync
**Service:** BE-SVC-AUDIT · **Handler:** `TZ-Tigo-SuperApp-AuditLogs/TZTigoSuperAppAuditLogs/Controllers/LogsController.cs › LogsController.CreateLogsAsync` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Logs/create
  internal_path: /api/Logs/create
  dispatch_field: null
  dispatch_value: null
  controller_action: LogsController.CreateLogsAsync
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| requestingOrganisationTransactionReference | `string?` | no | — | DataAnnotations / action | — |
| msisdn | `string?` | no | — | DataAnnotations / action | — |
| guid | `string?` | no | — | DataAnnotations / action | — |
| timestamp | `DateTime?` | no | — | DataAnnotations / action | — |
| operation_type | `string?` | no | — | DataAnnotations / action | — |
| amount | `double?` | no | — | DataAnnotations / action | — |
| targetmsisdn | `string?` | no | — | DataAnnotations / action | — |
| transaction_id | `string?` | no | — | DataAnnotations / action | — |
| status | `string?` | no | — | DataAnnotations / action | — |
| response_detail | `string?` | no | — | DataAnnotations / action | — |
| additional_info | `string?` | no | — | DataAnnotations / action | — |
| json_request | `string?` | no | — | DataAnnotations / action | — |
| json_response | `string?` | no | — | DataAnnotations / action | — |
| requestingOrganisationTransactionReference | `string?` | no | — | DataAnnotations / action | — |
| json_request | `string?` | no | — | DataAnnotations / action | — |
| Controller | `string?` | no | — | DataAnnotations / action | — |
| Method | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "requestingOrganisationTransactionReference": "<requestingOrganisationTransactionReference>", "msisdn": "<msisdn>", "guid": "<guid>", "timestamp": "<timestamp>", "operation_type": "<operation_type>", "amount": "<amount>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Guard: saved successfully | HTTP 200-envelope | — | `TZTigoSuperAppAuditLogs/Controllers/LogsController.cs › LogsController.CreateLogsAsync` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `LogsController.CreateLogsAsync`
2. Action body in `TZTigoSuperAppAuditLogs/Controllers/LogsController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as LogsController
  participant Svc as downstream
  App->>Ctrl: POST /api/Logs/create
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
| See service data-model | R/W | Traced at SHA eb87819 |

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
| — | 200-envelope | — | success=false envelope | saved successfully | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/audit/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-AuditLogs/TZTigoSuperAppAuditLogs/Controllers/LogsController.cs › LogsController.CreateLogsAsync` @ `eb87819`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
