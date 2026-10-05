---
kb_section: backend
type: api-contract
ids: [BE-API-EXPENSE-003]
service: EXPENSE
repo: TZ-Tigo-SuperApp-Expense
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: e821ac9
updated: 2026-10-05
confidence: confirmed
---
# BE-API-EXPENSE-003 AdvanceSalaryController.SalaryAdvanceRequest
**Service:** BE-SVC-EXPENSE · **Handler:** `TZ-Tigo-SuperApp-Expense/TZTigoSuperAppExpense/Controllers/AdvanceSalaryController.cs › AdvanceSalaryController.SalaryAdvanceRequest` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/AdvanceSalary
  internal_path: /api/AdvanceSalary
  dispatch_field: null
  dispatch_value: null
  controller_action: AdvanceSalaryController.SalaryAdvanceRequest
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** SalaryAdvanceRequest

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| Msisdn | `string?` | no | — | DataAnnotations / action | — |
| Amount | `float?` | no | — | DataAnnotations / action | — |
| EffectiveFrom | `string?` | no | — | DataAnnotations / action | — |
| Type | `string?` | no | — | DataAnnotations / action | — |
| PayUpto | `string?` | no | — | DataAnnotations / action | — |
| MSISDN | `string?` | no | — | DataAnnotations / action | — |
| Amount | `float?` | no | — | DataAnnotations / action | — |
| EffectiveFrom | `string?` | no | — | DataAnnotations / action | — |
| Type | `string?` | no | — | DataAnnotations / action | — |
| PayUpto | `string?` | no | — | DataAnnotations / action | — |
| ReferenceID | `string?` | no | — | DataAnnotations / action | — |
| RequestChannel | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "Msisdn": "<Msisdn>", "Amount": "<Amount>", "EffectiveFrom": "<EffectiveFrom>", "Type": "<Type>", "PayUpto": "<PayUpto>", "MSISDN": "<MSISDN>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `AdvanceSalaryController.SalaryAdvanceRequest`
2. Action body in `TZTigoSuperAppExpense/Controllers/AdvanceSalaryController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as AdvanceSalaryController
  participant Svc as downstream
  App->>Ctrl: POST /api/AdvanceSalary
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
| See service data-model | R/W | Traced at SHA e821ac9 |

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
| — | 500 | — | Unhandled exception | Internal error | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/expense/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Expense/TZTigoSuperAppExpense/Controllers/AdvanceSalaryController.cs › AdvanceSalaryController.SalaryAdvanceRequest` @ `e821ac9`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
