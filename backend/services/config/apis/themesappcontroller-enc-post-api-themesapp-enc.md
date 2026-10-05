---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-338]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-338 ThemesAppController.enc
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/ThemesAppController.cs › ThemesAppController.enc` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/ThemesApp/enc
  internal_path: /api/ThemesApp/enc
  dispatch_field: null
  dispatch_value: null
  controller_action: ThemesAppController.enc
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| requestingOrganisationTransactionReference | `string` | no | — | DataAnnotations / action | — |
| iPInfo | `string` | no | — | DataAnnotations / action | — |
| geoCode | `string` | no | — | DataAnnotations / action | — |
| useCaseName | `string` | no | — | DataAnnotations / action | — |
| channel | `string` | no | — | DataAnnotations / action | — |
| appVersion | `string` | no | — | DataAnnotations / action | — |
| languageCode | `string` | no | — | DataAnnotations / action | — |
| deviceId | `string` | no | — | DataAnnotations / action | — |
| deviceMaker | `string` | no | — | DataAnnotations / action | — |
| oS | `string` | no | — | DataAnnotations / action | — |
| accesstoken | `string` | no | — | DataAnnotations / action | — |
| deviceType | `string` | no | — | DataAnnotations / action | — |
| requestId | `string` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "requestingOrganisationTransactionReference": "<requestingOrganisationTransactionReference>", "iPInfo": "<iPInfo>", "geoCode": "<geoCode>", "useCaseName": "<useCaseName>", "channel": "<channel>", "appVersion": "<appVersion>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `ThemesAppController.enc`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/AppController/ThemesAppController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as ThemesAppController
  participant Svc as downstream
  App->>Ctrl: POST /api/ThemesApp/enc
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/ThemesAppController.cs › ThemesAppController.enc` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
