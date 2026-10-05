---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-403]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-403 LeaderboardAppController.Get
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/LeaderboardAppController.cs › LeaderboardAppController.Get` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/LeaderboardApp/get
  internal_path: /api/LeaderboardApp/get
  dispatch_field: null
  dispatch_value: null
  controller_action: LeaderboardAppController.Get
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
| 1 | Guard: success = true, statusCode = 200, transactionStatus = "Data Fetch Successfully", isEnabled, responseData  | HTTP 200 | — | `TZTigoSuperAppConfiguration/Controllers/AppController/LeaderboardAppController.cs › LeaderboardAppController.Get` |
| 2 | Guard: success = false, Data = ex.ToString(),  | HTTP 500 | — | `TZTigoSuperAppConfiguration/Controllers/AppController/LeaderboardAppController.cs › LeaderboardAppController.Get` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `LeaderboardAppController.Get`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/AppController/LeaderboardAppController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as LeaderboardAppController
  participant Svc as downstream
  App->>Ctrl: POST /api/LeaderboardApp/get
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
| — | 200 | — | reachable return | success = true, statusCode = 200, transactionStatus = "Data Fetch Successfully", isEnabled, responseData  | no |
| — | 500 | — | reachable return | success = false, Data = ex.ToString(),  | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/config/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/LeaderboardAppController.cs › LeaderboardAppController.Get` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
