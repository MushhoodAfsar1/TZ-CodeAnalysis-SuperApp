---
kb_section: backend
type: api-contract
ids: [BE-API-SELFC-030]
service: SELFC
repo: TZ-Tigo-SuperApp-SelfCare
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: a0aeca8
updated: 2026-10-05
confidence: confirmed
---
# BE-API-SELFC-030 SelfCareController.TransactionHistoryDetailV1
**Service:** BE-SVC-SELFC · **Handler:** `TZ-Tigo-SuperApp-SelfCare/TZTigoSuperAppSelfcare/Controllers/SelfCareController.cs › SelfCareController.TransactionHistoryDetailV1` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/SelfCare
  internal_path: /api/SelfCare
  dispatch_field: null
  dispatch_value: null
  controller_action: SelfCareController.TransactionHistoryDetailV1
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** TransactionHistoryRequestV1

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| msisdn | `string?` | no | — | DataAnnotations / action | — |
| mpin | `string?` | no | — | DataAnnotations / action | — |
| msisdn | `string?` | no | — | DataAnnotations / action | — |
| msisdn | `string?` | no | — | DataAnnotations / action | — |
| transDateFrom | `string?` | no | — | DataAnnotations / action | — |
| transDateTo | `string?` | no | — | DataAnnotations / action | — |
| limit | `int?` | no | — | DataAnnotations / action | — |
| brandName | `List<string>?` | no | — | DataAnnotations / action | — |
| duration | `string?` | no | — | DataAnnotations / action | — |
| email | `string?` | no | — | DataAnnotations / action | — |
| mpin | `string?` | no | — | DataAnnotations / action | — |
| downloadType | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "msisdn": "<msisdn>", "mpin": "<mpin>", "msisdn": "<msisdn>", "msisdn": "<msisdn>", "transDateFrom": "<transDateFrom>", "transDateTo": "<transDateTo>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `SelfCareController.TransactionHistoryDetailV1`
2. Action body in `TZTigoSuperAppSelfcare/Controllers/SelfCareController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as SelfCareController
  participant Svc as downstream
  App->>Ctrl: POST /api/SelfCare
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
| See service data-model | R/W | Traced at SHA a0aeca8 |

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
See `services/selfc/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-SelfCare/TZTigoSuperAppSelfcare/Controllers/SelfCareController.cs › SelfCareController.TransactionHistoryDetailV1` @ `a0aeca8`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
