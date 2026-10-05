---
kb_section: backend
type: api-contract
ids: [BE-API-ACCOUNT-020]
service: ACCOUNT
repo: TZ-Tigo-SuperApp-Account
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 5c549d6
updated: 2026-10-05
confidence: confirmed
---
# BE-API-ACCOUNT-020 ProfileController.DiasporaRegistration
**Service:** BE-SVC-ACCOUNT · **Handler:** `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/ProfileController.cs › ProfileController.DiasporaRegistration` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Profile
  internal_path: /api/Profile
  dispatch_field: null
  dispatch_value: null
  controller_action: ProfileController.DiasporaRegistration
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** InternationalRequest

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| action | `string?` | no | — | DataAnnotations / action | — |
| selfOnboardingDetails | `SelfOnboardingDetailsNew?` | no | — | DataAnnotations / action | — |
| selfOnboardingDocDetailS | `List<SelfOnboardingDocDetailS>?` | no | — | DataAnnotations / action | — |
| regMsisdn | `string?` | no | — | DataAnnotations / action | — |
| firstName | `string?` | no | — | DataAnnotations / action | — |
| middleName | `string?` | no | — | DataAnnotations / action | — |
| lastName | `string?` | no | — | DataAnnotations / action | — |
| dob | `string?` | no | — | DataAnnotations / action | — |
| gender | `string?` | no | — | DataAnnotations / action | — |
| city | `string?` | no | — | DataAnnotations / action | — |
| nationality | `string?` | no | — | DataAnnotations / action | — |
| email | `string?` | no | — | DataAnnotations / action | — |
| zipCode | `string?` | no | — | DataAnnotations / action | — |
| countryCode | `string?` | no | — | DataAnnotations / action | — |
| kycLevel | `string?` | no | — | DataAnnotations / action | — |
| shortCode | `string?` | no | — | DataAnnotations / action | — |
| occupation | `string?` | no | — | DataAnnotations / action | — |
| registrationFormNumber | `string?` | no | — | DataAnnotations / action | — |
| notificationNumber | `string?` | no | — | DataAnnotations / action | — |
| tinNumber | `string?` | no | — | DataAnnotations / action | — |
| vrnNumber | `string?` | no | — | DataAnnotations / action | — |
| vatRegistration | `string?` | no | — | DataAnnotations / action | — |
| birthCountryId | `string?` | no | — | DataAnnotations / action | — |
| countryNCode | `string?` | no | — | DataAnnotations / action | — |
| primaryIDType | `string?` | no | — | DataAnnotations / action | — |
| primaryIDNumber | `string?` | no | — | DataAnnotations / action | — |
| country | `string?` | no | — | DataAnnotations / action | — |
| fullName | `string?` | no | — | DataAnnotations / action | — |
| street | `string?` | no | — | DataAnnotations / action | — |
| neighborhood | `string?` | no | — | DataAnnotations / action | — |
| appVersion | `string?` | no | — | DataAnnotations / action | — |
| ChannelType | `string?` | no | — | DataAnnotations / action | — |
| customerMsisdn | `string?` | no | — | DataAnnotations / action | — |
| firstName | `string?` | no | — | DataAnnotations / action | — |
| middleName | `string?` | no | — | DataAnnotations / action | — |
| lastName | `string?` | no | — | DataAnnotations / action | — |
| dob | `string?` | no | — | DataAnnotations / action | — |
| gender | `string?` | no | — | DataAnnotations / action | — |
| placeofbirth | `string?` | no | — | DataAnnotations / action | — |
| address | `string?` | no | — | DataAnnotations / action | — |
| city | `string?` | no | — | DataAnnotations / action | — |
| district | `string?` | no | — | DataAnnotations / action | — |
| region | `string?` | no | — | DataAnnotations / action | — |
| nationality | `string?` | no | — | DataAnnotations / action | — |
| emailid | `string?` | no | — | DataAnnotations / action | — |
| spokenLanguage | `string?` | no | — | DataAnnotations / action | — |
| type | `string?` | no | — | DataAnnotations / action | — |
| latitude | `string?` | no | — | DataAnnotations / action | — |
| longitude | `string?` | no | — | DataAnnotations / action | — |
| zipCode | `string?` | no | — | DataAnnotations / action | — |
| documentExpiry | `string?` | no | — | DataAnnotations / action | — |
| documentNumber | `string?` | no | — | DataAnnotations / action | — |
| documentType | `string?` | no | — | DataAnnotations / action | — |
| status | `string?` | no | — | DataAnnotations / action | — |
| documentUrls | `List<DocumentUrls>?` | no | — | DataAnnotations / action | — |
| fileName | `string?` | no | — | DataAnnotations / action | — |
| image | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "action": "<action>", "selfOnboardingDetails": "<selfOnboardingDetails>", "selfOnboardingDocDetailS": "<selfOnboardingDocDetailS>", "regMsisdn": "<regMsisdn>", "firstName": "<firstName>", "middleName": "<middleName>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `ProfileController.DiasporaRegistration`
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
- `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/ProfileController.cs › ProfileController.DiasporaRegistration` @ `5c549d6`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
