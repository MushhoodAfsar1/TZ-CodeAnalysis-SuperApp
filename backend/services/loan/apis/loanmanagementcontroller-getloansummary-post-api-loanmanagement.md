---
kb_section: backend
type: api-contract
ids: [BE-API-LOAN-004]
service: LOAN
repo: TZ-Tigo-SuperApp-Loan
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 759a471
updated: 2026-10-05
confidence: confirmed
---
# BE-API-LOAN-004 LoanManagementController.GetLoanSummary
**Service:** BE-SVC-LOAN · **Handler:** `TZ-Tigo-SuperApp-Loan/TZTigoSuperAppLoan/Controllers/LoanManagementController.cs › LoanManagementController.GetLoanSummary` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/LoanManagement
  internal_path: /api/LoanManagement
  dispatch_field: null
  dispatch_value: null
  controller_action: LoanManagementController.GetLoanSummary
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** GetLoanSummaryRequest

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| consumerID | `string?` | no | — | DataAnnotations / action | — |
| referenceId | `string?` | no | — | DataAnnotations / action | — |
| customerMsisdn | `string?` | no | — | DataAnnotations / action | — |
| pin | `string?` | no | — | DataAnnotations / action | — |
| summarybrandID | `string?` | no | — | DataAnnotations / action | — |
| loanbrandID | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "consumerID": "<consumerID>", "referenceId": "<referenceId>", "customerMsisdn": "<customerMsisdn>", "pin": "<pin>", "summarybrandID": "<summarybrandID>", "loanbrandID": "<loanbrandID>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `LoanManagementController.GetLoanSummary`
2. Action body in `TZTigoSuperAppLoan/Controllers/LoanManagementController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as LoanManagementController
  participant Svc as downstream
  App->>Ctrl: POST /api/LoanManagement
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
| See service data-model | R/W | Traced at SHA 759a471 |

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
See `services/loan/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Loan/TZTigoSuperAppLoan/Controllers/LoanManagementController.cs › LoanManagementController.GetLoanSummary` @ `759a471`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
