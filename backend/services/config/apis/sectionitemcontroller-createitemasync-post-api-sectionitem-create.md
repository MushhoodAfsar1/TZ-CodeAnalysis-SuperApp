---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-223]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-223 SectionItemController.CreateItemAsync
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SectionItemController.cs › SectionItemController.CreateItemAsync` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/SectionItem/create
  internal_path: /api/SectionItem/create
  dispatch_field: null
  dispatch_value: null
  controller_action: SectionItemController.CreateItemAsync
  topic: null
```

## Exposure & security
- **Auth:** JWT
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| Id | `Int32` | no | — | DataAnnotations / action | — |
| section_name | `string` | no | — | DataAnnotations / action | — |
| image_url | `string` | no | — | DataAnnotations / action | — |
| sort_order | `Int32` | no | — | DataAnnotations / action | — |
| description | `string` | no | — | DataAnnotations / action | — |
| created_by | `string` | no | — | DataAnnotations / action | — |
| created_date | `DateTime` | no | — | DataAnnotations / action | — |
| updated_by | `string` | no | — | DataAnnotations / action | — |
| updated_date | `DateTime` | no | — | DataAnnotations / action | — |
| country_id | `Int32` | no | — | DataAnnotations / action | — |
| channel_id | `Int32` | no | — | DataAnnotations / action | — |
| app_version_id | `Int32` | no | — | DataAnnotations / action | — |
| flow_id | `string` | no | — | DataAnnotations / action | — |
| messages | `List<DashboardMultilingualMessage>` | no | — | DataAnnotations / action | — |
| image_size | `string` | no | — | DataAnnotations / action | — |
| image_type | `string` | no | — | DataAnnotations / action | — |
| image_name | `string` | no | — | DataAnnotations / action | — |
| displayon | `string?` | no | — | DataAnnotations / action | — |
| is_merchant_biller | `Boolean` | no | — | DataAnnotations / action | — |
| isrevamp | `bool` | no | — | DataAnnotations / action | — |
| Id | `Int32` | no | — | DataAnnotations / action | — |
| section_item_id | `Int32` | no | — | DataAnnotations / action | — |
| name | `string` | no | — | DataAnnotations / action | — |
| ussdCode | `string?` | no | — | DataAnnotations / action | — |
| shortCode | `string?` | no | — | DataAnnotations / action | — |
| code | `string?` | no | — | DataAnnotations / action | — |
| merchantShortCode | `string?` | no | — | DataAnnotations / action | — |
| segment1 | `string?` | no | — | DataAnnotations / action | — |
| segment2 | `string?` | no | — | DataAnnotations / action | — |
| segment3 | `string?` | no | — | DataAnnotations / action | — |
| segment4 | `string?` | no | — | DataAnnotations / action | — |
| image_url | `string` | no | — | DataAnnotations / action | — |
| dark_image_url | `string` | no | — | DataAnnotations / action | — |
| sort_order | `Int32` | no | — | DataAnnotations / action | — |
| newly_added | `Int32` | no | — | DataAnnotations / action | — |
| description | `string` | no | — | DataAnnotations / action | — |
| created_by | `string` | no | — | DataAnnotations / action | — |
| created_date | `DateTime` | no | — | DataAnnotations / action | — |
| updated_by | `string` | no | — | DataAnnotations / action | — |
| updated_date | `DateTime` | no | — | DataAnnotations / action | — |
| version_android | `string` | no | — | DataAnnotations / action | — |
| version_ios | `string` | no | — | DataAnnotations / action | — |
| messages | `List<DashboardMultilingualMessage>` | no | — | DataAnnotations / action | — |
| country_id | `Int32` | no | — | DataAnnotations / action | — |
| channel_id | `Int32` | no | — | DataAnnotations / action | — |
| app_version_id | `Int32` | no | — | DataAnnotations / action | — |
| flow_id | `string` | no | — | DataAnnotations / action | — |
| standardPrice | `string?` | no | — | DataAnnotations / action | — |
| xtraViewPvrPrice | `string?` | no | — | DataAnnotations / action | — |
| countryCode | `string?` | no | — | DataAnnotations / action | — |
| image_size | `string` | no | — | DataAnnotations / action | — |
| image_type | `string` | no | — | DataAnnotations / action | — |
| image_name | `string` | no | — | DataAnnotations / action | — |
| dark_image_size | `string` | no | — | DataAnnotations / action | — |
| dark_image_type | `string` | no | — | DataAnnotations / action | — |
| dark_image_name | `string` | no | — | DataAnnotations / action | — |
| starttimecheck | `string?` | no | — | DataAnnotations / action | — |
| endtimecheck | `string?` | no | — | DataAnnotations / action | — |
| reference_en | `string?` | no | — | DataAnnotations / action | — |
| reference_sw | `string?` | no | — | DataAnnotations / action | — |
| url | `string?` | no | — | DataAnnotations / action | — |
| time_check | `Boolean?` | no | — | DataAnnotations / action | — |
| isactive | `Boolean?` | no | — | DataAnnotations / action | — |
| isallowquickaction | `Boolean` | no | — | DataAnnotations / action | — |
| is_merchant_biller | `Boolean` | no | — | DataAnnotations / action | — |
| Id | `Int32` | no | — | DataAnnotations / action | — |
| section_id | `Int32` | no | — | DataAnnotations / action | — |
| name | `string` | no | — | DataAnnotations / action | — |
| image_url | `string` | no | — | DataAnnotations / action | — |
| dark_image_url | `string` | no | — | DataAnnotations / action | — |
| sort_order | `Int32` | no | — | DataAnnotations / action | — |
| description | `string` | no | — | DataAnnotations / action | — |
| version_android | `string` | no | — | DataAnnotations / action | — |
| version_ios | `string` | no | — | DataAnnotations / action | — |
| newly_added | `Int32` | no | — | DataAnnotations / action | — |
| created_by | `string` | no | — | DataAnnotations / action | — |
| created_date | `DateTime` | no | — | DataAnnotations / action | — |
| updated_by | `string` | no | — | DataAnnotations / action | — |
| updated_date | `DateTime` | no | — | DataAnnotations / action | — |
| country_id | `Int32` | no | — | DataAnnotations / action | — |
| channel_id | `Int32` | no | — | DataAnnotations / action | — |
| app_version_id | `Int32` | no | — | DataAnnotations / action | — |
| app_version_ios_id | `Int32` | no | — | DataAnnotations / action | — |
| app_version_hms_id | `Int32` | no | — | DataAnnotations / action | — |
| flow_id | `string` | no | — | DataAnnotations / action | — |
| messages | `List<DashboardMultilingualMessage>` | no | — | DataAnnotations / action | — |
| image_size | `string` | no | — | DataAnnotations / action | — |
| image_type | `string` | no | — | DataAnnotations / action | — |
| image_name | `string` | no | — | DataAnnotations / action | — |
| dark_image_size | `string` | no | — | DataAnnotations / action | — |
| dark_image_type | `string` | no | — | DataAnnotations / action | — |
| dark_image_name | `string` | no | — | DataAnnotations / action | — |
| starttimecheck | `string?` | no | — | DataAnnotations / action | — |
| endtimecheck | `string?` | no | — | DataAnnotations / action | — |
| reference_en | `string?` | no | — | DataAnnotations / action | — |
| reference_sw | `string?` | no | — | DataAnnotations / action | — |
| time_check | `Boolean?` | no | — | DataAnnotations / action | — |
| isactive | `Boolean?` | no | — | DataAnnotations / action | — |
| generalcode | `string?` | no | — | DataAnnotations / action | — |
| shortcode | `string?` | no | — | DataAnnotations / action | — |
| code | `string?` | no | — | DataAnnotations / action | — |
| isallowquickaction | `Boolean` | no | — | DataAnnotations / action | — |
| is_merchant_biller | `Boolean` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "Id": "<Id>", "section_name": "<section_name>", "image_url": "<image_url>", "sort_order": "<sort_order>", "description": "<description>", "created_by": "<created_by>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | JWT via `X-User-Session` / Bearer | 401 | — | `TZTigoSuperAppConfiguration/Controllers/BO/SectionItemController.cs › SectionItemController` |
| 2 | Guard: saved successfully | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/SectionItemController.cs › SectionItemController.CreateItemAsync` |
| 3 | Guard: some error occurred | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/SectionItemController.cs › SectionItemController.CreateItemAsync` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `SectionItemController.CreateItemAsync`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/BO/SectionItemController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as SectionItemController
  participant Svc as downstream
  App->>Ctrl: POST /api/SectionItem/create
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
| — | 200-envelope | — | success=false envelope | saved successfully | no |
| — | 200-envelope | — | success=false envelope | some error occurred | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/config/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SectionItemController.cs › SectionItemController.CreateItemAsync` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
