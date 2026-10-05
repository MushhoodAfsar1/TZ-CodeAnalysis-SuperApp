---
kb_section: backend
type: api-contract
ids: [BE-API-ACCOUNT-012]
service: ACCOUNT
repo: TZ-Tigo-SuperApp-Account
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 5c549d6
updated: 2026-10-05
confidence: confirmed
---
# BE-API-ACCOUNT-012 ProfileController.Registration
**Service:** BE-SVC-ACCOUNT · **Handler:** `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/ProfileController.cs › ProfileController.Registration` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Profile
  internal_path: /api/Profile
  dispatch_field: null
  dispatch_value: null
  controller_action: ProfileController.Registration
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** RegistrationRequest

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| msisdn | `string?` | no | — | DataAnnotations / action | — |
| firstName | `string?` | no | — | DataAnnotations / action | — |
| middleName | `string?` | no | — | DataAnnotations / action | — |
| lastName | `string?` | no | — | DataAnnotations / action | — |
| dateOfBirth | `string?` | no | — | DataAnnotations / action | — |
| gender | `string?` | no | — | DataAnnotations / action | — |
| placeofbirth | `string?` | no | — | DataAnnotations / action | — |
| address | `string?` | no | — | DataAnnotations / action | — |
| city | `string?` | no | — | DataAnnotations / action | — |
| district | `string?` | no | — | DataAnnotations / action | — |
| region | `string?` | no | — | DataAnnotations / action | — |
| nationality | `string?` | no | — | DataAnnotations / action | — |
| emailid | `string?` | no | — | DataAnnotations / action | — |
| profileimage | `string?` | no | — | DataAnnotations / action | — |
| nicfrontimage | `string?` | no | — | DataAnnotations / action | — |
| nicbackimage | `string?` | no | — | DataAnnotations / action | — |
| newMpin | `string?` | no | — | DataAnnotations / action | — |
| confirmMpin | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "msisdn": "<msisdn>", "firstName": "<firstName>", "middleName": "<middleName>", "lastName": "<lastName>", "dateOfBirth": "<dateOfBirth>", "gender": "<gender>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `ProfileController.Registration`
2. Action body in `TZTigoSuperAppAccount/Controllers/ProfileController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as ProfileController
  participant Svc as downstream
  App->>Ctrl: POST /api/Profile
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
- `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/ProfileController.cs › ProfileController.Registration` @ `5c549d6`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
