---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-360]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-360 AppCardsController.GetAllItems
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/AppCardsController.cs › AppCardsController.GetAllItems` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/AppCards/GetAllItems
  internal_path: /api/AppCards/GetAllItems
  dispatch_field: null
  dispatch_value: null
  controller_action: AppCardsController.GetAllItems
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** BaseModelRequest

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
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
| 1 | Guard: success = cacheData.success, responseCode = cacheData.responseCode, responseData = cacheData.Data  | HTTP 200 | — | `TZTigoSuperAppConfiguration/Controllers/AppController/AppCardsController.cs › AppCardsController.GetAllItems` |
| 2 | Guard: success = response.success, responseCode = response.responseCode, responseData = response.Data  | HTTP 200 | — | `TZTigoSuperAppConfiguration/Controllers/AppController/AppCardsController.cs › AppCardsController.GetAllItems` |
| 3 | Guard: success = false, responseCode = "99", responseMessage_en = "An error occurred while fetching home config"  | HTTP 500 | — | `TZTigoSuperAppConfiguration/Controllers/AppController/AppCardsController.cs › AppCardsController.GetAllItems` |
| 4 | Guard: An error occurred while fetching home config | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/AppController/AppCardsController.cs › AppCardsController.GetAllItems` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `AppCardsController.GetAllItems`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/AppController/AppCardsController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as AppCardsController
  participant Svc as downstream
  App->>Ctrl: POST /api/AppCards/GetAllItems
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
| — | 200 | — | reachable return | success = cacheData.success, responseCode = cacheData.responseCode, responseData = cacheData.Data  | no |
| — | 200 | — | reachable return | success = response.success, responseCode = response.responseCode, responseData = response.Data  | no |
| — | 500 | — | reachable return | success = false, responseCode = "99", responseMessage_en = "An error occurred while fetching home config"  | no |
| — | 200-envelope | — | success=false envelope | An error occurred while fetching home config | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/config/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/AppCardsController.cs › AppCardsController.GetAllItems` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
