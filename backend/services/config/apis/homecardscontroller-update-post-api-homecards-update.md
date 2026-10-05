---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-017]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-017 HomeCardsController.Update
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/HomeCardsController.cs › HomeCardsController.Update` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/HomeCards/update
  internal_path: /api/HomeCards/update
  dispatch_field: null
  dispatch_value: null
  controller_action: HomeCardsController.Update
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
| card_id | `string` | no | — | DataAnnotations / action | — |
| card_type | `string` | no | — | DataAnnotations / action | — |
| enabled | `bool` | no | — | DataAnnotations / action | — |
| sort_order | `int` | no | — | DataAnnotations / action | — |
| is_default | `bool` | no | — | DataAnnotations / action | — |
| title | `string?` | no | — | DataAnnotations / action | — |
| subtitle | `string?` | no | — | DataAnnotations / action | — |
| dashboard_layout_id | `int?` | no | — | DataAnnotations / action | — |
| created_by | `string?` | no | — | DataAnnotations / action | — |
| created_date | `DateTime?` | no | — | DataAnnotations / action | — |
| updated_by | `string?` | no | — | DataAnnotations / action | — |
| updated_date | `DateTime?` | no | — | DataAnnotations / action | — |
| cardId | `string` | no | — | DataAnnotations / action | — |
| type | `string` | no | — | DataAnnotations / action | — |
| enabled | `bool` | no | — | DataAnnotations / action | — |
| order | `int` | no | — | DataAnnotations / action | — |
| isDefault | `bool` | no | — | DataAnnotations / action | — |
| title | `string?` | no | — | DataAnnotations / action | — |
| subtitle | `string?` | no | — | DataAnnotations / action | — |
| cardId | `string` | no | — | DataAnnotations / action | — |
| cardType | `string` | no | — | DataAnnotations / action | — |
| enabled | `bool` | no | — | DataAnnotations / action | — |
| sortOrder | `int` | no | — | DataAnnotations / action | — |
| sections | `List<HomeLayoutSectionInCardAppDto>` | no | — | DataAnnotations / action | — |
| cards | `List<HomeCarouselCardAppDto>` | no | — | DataAnnotations / action | — |
| cards | `List<HomeCarouselCardWithSectionsAppDto>` | no | — | DataAnnotations / action | — |
| footerConfig | `List<FooterConfigAppDto>?` | no | — | DataAnnotations / action | — |
| cards | `List<HomeCarouselCardWithSectionsAppDto>` | no | — | DataAnnotations / action | — |
| footerConfig | `List<FooterConfigAppDto>?` | no | — | DataAnnotations / action | — |
| drawerItems | `List<MenuItemAppDto>` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "Id": "<Id>", "card_id": "<card_id>", "card_type": "<card_type>", "enabled": "<enabled>", "sort_order": "<sort_order>", "is_default": "<is_default>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | JWT via `X-User-Session` / Bearer | 401 | — | `TZTigoSuperAppConfiguration/Controllers/BO/HomeCardsController.cs › HomeCardsController` |
| 2 | Guard: Card ID already exists | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/HomeCardsController.cs › HomeCardsController.Update` |
| 3 | Guard: Sort order already exists | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/HomeCardsController.cs › HomeCardsController.Update` |
| 4 | Guard: An error occurred | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/HomeCardsController.cs › HomeCardsController.Update` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `HomeCardsController.Update`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/BO/HomeCardsController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as HomeCardsController
  participant Svc as downstream
  App->>Ctrl: POST /api/HomeCards/update
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
| — | 200-envelope | — | success=false envelope | Card ID already exists | no |
| — | 200-envelope | — | success=false envelope | Sort order already exists | no |
| — | 200-envelope | — | success=false envelope | An error occurred | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/config/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/HomeCardsController.cs › HomeCardsController.Update` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
