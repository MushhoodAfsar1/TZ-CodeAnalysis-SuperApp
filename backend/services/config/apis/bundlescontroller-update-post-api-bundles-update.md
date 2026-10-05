---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-200]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-200 BundlesController.Update
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BundlesController.cs › BundlesController.Update` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Bundles/update
  internal_path: /api/Bundles/update
  dispatch_field: null
  dispatch_value: null
  controller_action: BundlesController.Update
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
| FileName | `string?` | no | — | DataAnnotations / action | — |
| FileExtension | `string?` | no | — | DataAnnotations / action | — |
| MimeType | `string?` | no | — | DataAnnotations / action | — |
| FilePath | `string?` | no | — | DataAnnotations / action | — |
| saiziYakoBundles | `BundlesResponse?` | no | — | DataAnnotations / action | — |
| boBundles | `List<BundleDto>?` | no | — | DataAnnotations / action | — |
| boBundles | `List<BundleDto>?` | no | — | DataAnnotations / action | — |
| boBundles | `List<BundleDto>?` | no | — | DataAnnotations / action | — |
| saiziYakoBundles | `BundlesResponse?` | no | — | DataAnnotations / action | — |
| id | `int` | no | — | DataAnnotations / action | — |
| engCategory | `string?` | no | — | DataAnnotations / action | — |
| swCategory | `string?` | no | — | DataAnnotations / action | — |
| enPackName | `string?` | no | — | DataAnnotations / action | — |
| swPackName | `string?` | no | — | DataAnnotations / action | — |
| productId | `string?` | no | — | DataAnnotations / action | — |
| ffeId | `string?` | no | — | DataAnnotations / action | — |
| engValidity | `string?` | no | — | DataAnnotations / action | — |
| swValidity | `string?` | no | — | DataAnnotations / action | — |
| data | `string?` | no | — | DataAnnotations / action | — |
| levelIDisplay | `string?` | no | — | DataAnnotations / action | — |
| levelIIDisplay | `string?` | no | — | DataAnnotations / action | — |
| dataUnit | `string?` | no | — | DataAnnotations / action | — |
| voiceUnit | `string?` | no | — | DataAnnotations / action | — |
| unit | `string?` | no | — | DataAnnotations / action | — |
| price | `string?` | no | — | DataAnnotations / action | — |
| engDescription | `string?` | no | — | DataAnnotations / action | — |
| swDescription | `string?` | no | — | DataAnnotations / action | — |
| simCategory | `bool?` | no | — | DataAnnotations / action | — |
| category | `string?` | no | — | DataAnnotations / action | — |
| type | `string?` | no | — | DataAnnotations / action | — |
| typesw | `string?` | no | — | DataAnnotations / action | — |
| bundleClass | `string?` | no | — | DataAnnotations / action | — |
| action | `string?` | no | — | DataAnnotations / action | — |
| levelIDisplaySwahili | `string?` | no | — | DataAnnotations / action | — |
| levelIDisplayEnglish | `string?` | no | — | DataAnnotations / action | — |
| levelIIDisplayEnglish | `string?` | no | — | DataAnnotations / action | — |
| levelIIDisplaySwahili | `string?` | no | — | DataAnnotations / action | — |
| dataUnitEnglish | `string?` | no | — | DataAnnotations / action | — |
| dataUnitSwahili | `string?` | no | — | DataAnnotations / action | — |
| voice | `string?` | no | — | DataAnnotations / action | — |
| voiceUnitEnglish | `string?` | no | — | DataAnnotations / action | — |
| voiceUnitSwahili | `string?` | no | — | DataAnnotations / action | — |
| sms | `string?` | no | — | DataAnnotations / action | — |
| tpProductId | `string?` | no | — | DataAnnotations / action | — |
| cbsProductId | `string?` | no | — | DataAnnotations / action | — |
| tpFfeId | `string?` | no | — | DataAnnotations / action | — |
| giftFfeId | `string?` | no | — | DataAnnotations / action | — |
| cbsFfeId | `string?` | no | — | DataAnnotations / action | — |
| subscriber | `string?` | no | — | DataAnnotations / action | — |
| operatorType | `string?` | no | — | DataAnnotations / action | — |
| isShowYasDashboard | `bool?` | no | — | DataAnnotations / action | — |
| jsonFile | `string?` | no | — | DataAnnotations / action | — |
| id | `int` | no | — | DataAnnotations / action | — |
| engCategory | `string?` | no | — | DataAnnotations / action | — |
| swCategory | `string?` | no | — | DataAnnotations / action | — |
| enPackName | `string?` | no | — | DataAnnotations / action | — |
| swPackName | `string?` | no | — | DataAnnotations / action | — |
| productId | `string?` | no | — | DataAnnotations / action | — |
| ffeId | `string?` | no | — | DataAnnotations / action | — |
| engValidity | `string?` | no | — | DataAnnotations / action | — |
| swValidity | `string?` | no | — | DataAnnotations / action | — |
| data | `string?` | no | — | DataAnnotations / action | — |
| price | `string?` | no | — | DataAnnotations / action | — |
| engDescription | `string?` | no | — | DataAnnotations / action | — |
| swDescription | `string?` | no | — | DataAnnotations / action | — |
| simCategory | `bool?` | no | — | DataAnnotations / action | — |
| id | `int` | no | — | DataAnnotations / action | — |
| category | `string?` | no | — | DataAnnotations / action | — |
| type | `string?` | no | — | DataAnnotations / action | — |
| action | `string?` | no | — | DataAnnotations / action | — |
| price | `string?` | no | — | DataAnnotations / action | — |
| levelIDisplay | `string?` | no | — | DataAnnotations / action | — |
| levelIIDisplay | `string?` | no | — | DataAnnotations / action | — |
| tpProductId | `string?` | no | — | DataAnnotations / action | — |
| cbsProductId | `string?` | no | — | DataAnnotations / action | — |
| tpFfeId | `string?` | no | — | DataAnnotations / action | — |
| giftFfeId | `string?` | no | — | DataAnnotations / action | — |
| cbsFfeId | `string?` | no | — | DataAnnotations / action | — |
| subscriber | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "Id": "<Id>", "FileName": "<FileName>", "FileExtension": "<FileExtension>", "MimeType": "<MimeType>", "FilePath": "<FilePath>", "saiziYakoBundles": "<saiziYakoBundles>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | JWT via `X-User-Session` / Bearer | 401 | — | `TZTigoSuperAppConfiguration/Controllers/BO/BundlesController.cs › BundlesController` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `BundlesController.Update`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/BO/BundlesController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as BundlesController
  participant Svc as downstream
  App->>Ctrl: POST /api/Bundles/update
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BundlesController.cs › BundlesController.Update` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
