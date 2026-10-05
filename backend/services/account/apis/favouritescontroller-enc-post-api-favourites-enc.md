---
kb_section: backend
type: api-contract
ids: [BE-API-ACCOUNT-040]
service: ACCOUNT
repo: TZ-Tigo-SuperApp-Account
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 5c549d6
updated: 2026-10-05
confidence: confirmed
---
# BE-API-ACCOUNT-040 FavouritesController.enc
**Service:** BE-SVC-ACCOUNT · **Handler:** `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.enc` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Favourites/enc
  internal_path: /api/Favourites/enc
  dispatch_field: null
  dispatch_value: null
  controller_action: FavouritesController.enc
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| id | `int` | no | — | DataAnnotations / action | — |
| msisdn | `string` | no | — | DataAnnotations / action | — |
| flowId | `string` | no | — | DataAnnotations / action | — |
| jsonRequest | `dynamic` | no | — | DataAnnotations / action | — |
| uniqueId | `string` | no | — | DataAnnotations / action | — |
| operationType | `string` | no | — | DataAnnotations / action | — |
| sectionItemId | `int?` | no | — | DataAnnotations / action | — |
| subsectionItemId | `int?` | no | — | DataAnnotations / action | — |
| lightImageUrl | `string?` | no | — | DataAnnotations / action | — |
| darkImageUrl | `string?` | no | — | DataAnnotations / action | — |
| flowId | `string` | no | — | DataAnnotations / action | — |
| msisdn | `string` | no | — | DataAnnotations / action | — |
| id | `int` | no | — | DataAnnotations / action | — |
| msisdn | `string` | no | — | DataAnnotations / action | — |
| flowId | `string` | no | — | DataAnnotations / action | — |
| jsonRequest | `string` | no | — | DataAnnotations / action | — |
| uniqueId | `string` | no | — | DataAnnotations / action | — |
| operationType | `string` | no | — | DataAnnotations / action | — |
| lightImageUrl | `string` | no | — | DataAnnotations / action | — |
| darkImageUrl | `string` | no | — | DataAnnotations / action | — |
| sectionItemId | `int?` | no | — | DataAnnotations / action | — |
| subsectionItemId | `int?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "id": "<id>", "msisdn": "<msisdn>", "flowId": "<flowId>", "jsonRequest": "<jsonRequest>", "uniqueId": "<uniqueId>", "operationType": "<operationType>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `FavouritesController.enc`
2. Action body in `TZTigoSuperAppAccount/Controllers/FavouritesController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as FavouritesController
  participant Svc as downstream
  App->>Ctrl: POST /api/Favourites/enc
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
| See service data-model | R/W | Traced at SHA 5c549d6 |

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
See `services/account/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.enc` @ `5c549d6`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
