---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-397]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-397 MerchantManagementAppController.UpdatePrivileges
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/MerchantManagementAppController.cs › MerchantManagementAppController.UpdatePrivileges` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/MerchantManagementApp/UpdatePrivileges
  internal_path: /api/MerchantManagementApp/UpdatePrivileges
  dispatch_field: null
  dispatch_value: null
  controller_action: MerchantManagementAppController.UpdatePrivileges
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** MerchantRequestDto

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| msisdn | `string` | no | — | DataAnnotations / action | — |
| requestingOrganisationTransactionReference | `string?` | no | — | DataAnnotations / action | — |
| merchantmsisdn | `string` | no | — | DataAnnotations / action | — |
| usermsisdn | `string` | no | — | DataAnnotations / action | — |
| options | `List<Option>?` | no | — | DataAnnotations / action | — |
| country | `string?` | no | — | DataAnnotations / action | — |
| notificationnumber | `string?` | no | — | DataAnnotations / action | — |
| language | `string?` | no | — | DataAnnotations / action | — |
| requestId | `string?` | no | — | DataAnnotations / action | — |
| optionid | `int` | no | — | DataAnnotations / action | — |
| optionname | `string` | no | — | DataAnnotations / action | — |
| Body | `Body` | no | — | DataAnnotations / action | — |
| CreateMFSAccountUsernameResponse | `CreateMFSAccountUsernameResponse` | no | — | DataAnnotations / action | — |
| ResponseHeader | `ResponseHeader` | no | — | DataAnnotations / action | — |
| GeneralResponse | `GeneralResponse` | no | — | DataAnnotations / action | — |
| CorrelationID | `string` | no | — | DataAnnotations / action | — |
| Status | `string` | no | — | DataAnnotations / action | — |
| Code | `string` | no | — | DataAnnotations / action | — |
| Description | `string` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "msisdn": "<msisdn>", "requestingOrganisationTransactionReference": "<requestingOrganisationTransactionReference>", "merchantmsisdn": "<merchantmsisdn>", "usermsisdn": "<usermsisdn>", "options": "<options>", "country": "<country>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `MerchantManagementAppController.UpdatePrivileges`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/AppController/MerchantManagementAppController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as MerchantManagementAppController
  participant Svc as downstream
  App->>Ctrl: POST /api/MerchantManagementApp/UpdatePrivileges
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/MerchantManagementAppController.cs › MerchantManagementAppController.UpdatePrivileges` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
