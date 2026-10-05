---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-326]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-326 AppVersionsController.UpdateAppVersion
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AppVersionsController.cs › AppVersionsController.UpdateAppVersion` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/AppVersions
  internal_path: /api/AppVersions
  dispatch_field: null
  dispatch_value: null
  controller_action: AppVersionsController.UpdateAppVersion
  topic: null
```

## Exposure & security
- **Auth:** JWT
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| Id | `int` | no | — | DataAnnotations / action | — |
| Version | `string?` | no | — | DataAnnotations / action | — |
| UpdateSoft | `bool` | no | — | DataAnnotations / action | — |
| UpdateHard | `bool` | no | — | DataAnnotations / action | — |
| MessageSoftUpdate | `string?` | no | — | DataAnnotations / action | — |
| MessageHardUpdate | `string?` | no | — | DataAnnotations / action | — |
| CreatedBy | `string?` | no | — | DataAnnotations / action | — |
| CreatedDate | `DateTime` | no | — | DataAnnotations / action | — |
| UpdateBy | `string?` | no | — | DataAnnotations / action | — |
| UpdatedDate | `DateTime?` | no | — | DataAnnotations / action | — |
| Deleted | `bool` | no | — | DataAnnotations / action | — |
| AppTypeID | `long` | no | — | DataAnnotations / action | — |
| ChannelsId | `long` | no | — | DataAnnotations / action | — |
| CountryId | `int` | no | — | DataAnnotations / action | — |
| appchannelos | `string?` | no | — | DataAnnotations / action | — |
| translationsMessages | `List<TranslationsMessages>?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "Id": "<Id>", "Version": "<Version>", "UpdateSoft": "<UpdateSoft>", "UpdateHard": "<UpdateHard>", "MessageSoftUpdate": "<MessageSoftUpdate>", "MessageHardUpdate": "<MessageHardUpdate>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | JWT via `X-User-Session` / Bearer | 401 | — | `TZTigoSuperAppConfiguration/Controllers/BO/AppVersionsController.cs › AppVersionsController` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `AppVersionsController.UpdateAppVersion`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/BO/AppVersionsController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as AppVersionsController
  participant Svc as downstream
  App->>Ctrl: POST /api/AppVersions
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/AppVersionsController.cs › AppVersionsController.UpdateAppVersion` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
