---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-192]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-192 MenuItemsController.Create
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MenuItemsController.cs › MenuItemsController.Create` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/MenuItems/create
  internal_path: /api/MenuItems/create
  dispatch_field: null
  dispatch_value: null
  controller_action: MenuItemsController.Create
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
| menu_item_id | `string` | no | — | DataAnnotations / action | — |
| title_en | `string?` | no | — | DataAnnotations / action | — |
| title_sw | `string?` | no | — | DataAnnotations / action | — |
| enabled | `bool` | no | — | DataAnnotations / action | — |
| sort_order | `int` | no | — | DataAnnotations / action | — |
| icon_light | `string?` | no | — | DataAnnotations / action | — |
| icon_dark | `string?` | no | — | DataAnnotations / action | — |
| has_toggle | `bool` | no | — | DataAnnotations / action | — |
| toggle_enabled | `bool` | no | — | DataAnnotations / action | — |
| parent_id | `int?` | no | — | DataAnnotations / action | — |
| created_by | `string?` | no | — | DataAnnotations / action | — |
| created_date | `DateTime?` | no | — | DataAnnotations / action | — |
| updated_by | `string?` | no | — | DataAnnotations / action | — |
| updated_date | `DateTime?` | no | — | DataAnnotations / action | — |
| subItems | `List<MenuItemDto>?` | no | — | DataAnnotations / action | — |
| menuItemId | `string` | no | — | DataAnnotations / action | — |
| title | `string?` | no | — | DataAnnotations / action | — |
| order | `int` | no | — | DataAnnotations / action | — |
| iconLight | `string?` | no | — | DataAnnotations / action | — |
| iconDark | `string?` | no | — | DataAnnotations / action | — |
| hasToggle | `bool` | no | — | DataAnnotations / action | — |
| toggleEnabled | `bool` | no | — | DataAnnotations / action | — |
| subItems | `List<MenuItemAppDto>?` | no | — | DataAnnotations / action | — |
| drawerItems | `List<MenuItemAppDto>` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "Id": "<Id>", "menu_item_id": "<menu_item_id>", "title_en": "<title_en>", "title_sw": "<title_sw>", "enabled": "<enabled>", "sort_order": "<sort_order>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | JWT via `X-User-Session` / Bearer | 401 | — | `TZTigoSuperAppConfiguration/Controllers/BO/MenuItemsController.cs › MenuItemsController` |
| 2 | Guard: Menu item ID already exists | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/MenuItemsController.cs › MenuItemsController.Create` |
| 3 | Guard: Sort order already exists at this level | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/MenuItemsController.cs › MenuItemsController.Create` |
| 4 | Guard: An error occurred | HTTP 200-envelope | — | `TZTigoSuperAppConfiguration/Controllers/BO/MenuItemsController.cs › MenuItemsController.Create` |


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `MenuItemsController.Create`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/BO/MenuItemsController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as MenuItemsController
  participant Svc as downstream
  App->>Ctrl: POST /api/MenuItems/create
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
| — | 200-envelope | — | success=false envelope | Menu item ID already exists | no |
| — | 200-envelope | — | success=false envelope | Sort order already exists at this level | no |
| — | 200-envelope | — | success=false envelope | An error occurred | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/config/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MenuItemsController.cs › MenuItemsController.Create` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
