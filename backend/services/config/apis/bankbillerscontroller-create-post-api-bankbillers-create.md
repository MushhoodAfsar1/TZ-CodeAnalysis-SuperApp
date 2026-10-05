---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-059]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-059 BankBillersController.Create
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.Create` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/BankBillers/create
  internal_path: /api/BankBillers/create
  dispatch_field: null
  dispatch_value: null
  controller_action: BankBillersController.Create
  topic: null
```

## Exposure & security
- **Auth:** JWT
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| id | `int` | no | — | DataAnnotations / action | — |
| bankId | `int?` | no | — | DataAnnotations / action | — |
| billerId | `int?` | no | — | DataAnnotations / action | — |
| name | `string?` | no | — | DataAnnotations / action | — |
| code | `string?` | no | — | DataAnnotations / action | — |
| shortCode | `string?` | no | — | DataAnnotations / action | — |
| nameCheck | `string?` | no | — | DataAnnotations / action | — |
| ussdNumber | `string?` | no | — | DataAnnotations / action | — |
| ussdCode | `string?` | no | — | DataAnnotations / action | — |
| merchantShortCode | `string?` | no | — | DataAnnotations / action | — |
| segment1 | `string?` | no | — | DataAnnotations / action | — |
| segment2 | `string?` | no | — | DataAnnotations / action | — |
| categoryId | `string?` | no | — | DataAnnotations / action | — |
| companyOrder | `string?` | no | — | DataAnnotations / action | — |
| useViewBil | `string?` | no | — | DataAnnotations / action | — |
| status | `string?` | no | — | DataAnnotations / action | — |
| type | `string?` | no | — | DataAnnotations / action | — |
| imageUrl | `string?` | no | — | DataAnnotations / action | — |
| imageName | `string?` | no | — | DataAnnotations / action | — |
| imageSize | `string?` | no | — | DataAnnotations / action | — |
| imageType | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "id": "<id>", "bankId": "<bankId>", "billerId": "<billerId>", "name": "<name>", "code": "<code>", "shortCode": "<shortCode>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | JWT via `X-User-Session` / Bearer | 401 | — | `TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `BankBillersController.Create`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as BankBillersController
  participant Svc as downstream
  App->>Ctrl: POST /api/BankBillers/create
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
| — | 500 | — | Unhandled exception | Internal error | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/config/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.Create` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
