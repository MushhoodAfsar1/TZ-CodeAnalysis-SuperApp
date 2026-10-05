---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-243]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-243 SectionItemController.SaveSectionItemAsync
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SectionItemController.cs › SectionItemController.SaveSectionItemAsync` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/SectionItem/update
  internal_path: /api/SectionItem/update
  dispatch_field: null
  dispatch_value: null
  controller_action: SectionItemController.SaveSectionItemAsync
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/SectionItem/update`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `Id` | `Int32` | N | — | shape only | Id |
| `section_id` | `Int32` | N | — | shape only | section_id |
| `name` | `string` | N | — | shape only | name |
| `image_url` | `string` | N | — | shape only | image_url |
| `dark_image_url` | `string` | N | — | shape only | dark_image_url |
| `sort_order` | `Int32` | N | — | shape only | sort_order |
| `description` | `string` | N | — | shape only | description |
| `version_android` | `string` | N | — | shape only | version_android |
| `version_ios` | `string` | N | — | shape only | version_ios |
| `newly_added` | `Int32` | N | — | shape only | newly_added |
| `created_by` | `string` | N | — | shape only | created_by |
| `created_date` | `DateTime` | N | — | shape only | created_date |
| `updated_by` | `string` | N | — | shape only | updated_by |
| `updated_date` | `DateTime` | N | — | shape only | updated_date |
| `country_id` | `Int32` | N | — | shape only | country_id |
| `channel_id` | `Int32` | N | — | shape only | channel_id |
| `app_version_id` | `Int32` | N | — | shape only | app_version_id |
| `app_version_ios_id` | `Int32` | N | — | shape only | app_version_ios_id |
| `app_version_hms_id` | `Int32` | N | — | shape only | app_version_hms_id |
| `flow_id` | `string` | N | — | shape only | flow_id |
| `messages` | `List<DashboardMultilingualMessage>` | N | — | shape only | messages |
| `image_size` | `string` | N | — | shape only | image_size |
| `image_type` | `string` | N | — | shape only | image_type |
| `image_name` | `string` | N | — | shape only | image_name |
| `dark_image_size` | `string` | N | — | shape only | dark_image_size |
| `dark_image_type` | `string` | N | — | shape only | dark_image_type |
| `dark_image_name` | `string` | N | — | shape only | dark_image_name |
| `starttimecheck` | `string?` | N | — | shape only | starttimecheck |
| `endtimecheck` | `string?` | N | — | shape only | endtimecheck |
| `reference_en` | `string?` | N | — | shape only | reference_en |
| `reference_sw` | `string?` | N | — | shape only | reference_sw |
| `time_check` | `Boolean?` | N | — | shape only | time_check |
| `isactive` | `Boolean?` | N | — | shape only | isactive |
| `generalcode` | `string?` | N | — | shape only | generalcode |
| `shortcode` | `string?` | N | — | shape only | shortcode |
| `code` | `string?` | N | — | shape only | code |
| `isallowquickaction` | `Boolean` | N | — | shape only | isallowquickaction |
| `is_merchant_biller` | `Boolean` | N | — | shape only | is_merchant_biller |

Headers / route / query params: none parsed beyond action signature `[('section_item_dto', 'SectionItemDto')]`

Sample (synthetic):
```json
{
  "Id": 0,
  "section_id": 0,
  "name": "<string>",
  "image_url": "<string>",
  "dark_image_url": "<string>",
  "sort_order": 0,
  "description": "<string>",
  "version_android": "<string>",
  "version_ios": "<string>",
  "newly_added": 0,
  "created_by": "<string>",
  "created_date": "<iso-datetime>",
  "updated_by": "<string>",
  "updated_date": "<iso-datetime>",
  "country_id": 0,
  "channel_id": 0,
  "app_version_id": 0,
  "app_version_ios_id": 0,
  "app_version_hms_id": 0,
  "flow_id": "<string>",
  "messages": [],
  "image_size": "<string>",
  "image_type": "<string>",
  "image_name": "<string>",
  "dark_image_size": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `(section_item_db != null && section_item_db.image_url != section_item_dto.image_url` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SectionItemController.cs › SectionItemController.SaveSectionItemAsync` |
| 2 | `section_item_dto.image_url != null && (section_item_dto.image_url.Contains("data:image"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SectionItemController.cs › SectionItemController.SaveSectionItemAsync` |
| 3 | `!validationResult.IsValid` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SectionItemController.cs › SectionItemController.SaveSectionItemAsync` |
| 4 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SectionItemController.cs › SectionItemController.SaveSectionItemAsync` |

## Internal call chain
1. Client POST `/api/SectionItem/update`.
2. `SectionItemController.SaveSectionItemAsync` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SectionItemController.cs`).
3. Calls `_logger.LogDebug`.
4. Calls `MethodBase.GetCurrentMethod`.
5. Calls `MethodBase.GetCurrentMethod`.
6. Calls `Diagnostics.StackFrame`.
7. Calls `_sectionItemRepository.GetById`.
8. Calls `String.IsNullOrEmpty`.
9. Calls `image_url.Contains`.
10. Calls `image_url.Contains`.
11. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>SectionItemController: POST /api/SectionItem/update
  participant SectionItemController
  SectionItemController->>_logger: LogDebug()
  SectionItemController->>MethodBase: GetCurrentMethod()
  SectionItemController->>section_item_dto: ToString()
  SectionItemController->>Diagnostics: StackFrame()
  SectionItemController->>_sectionItemRepository: GetById()
  SectionItemController->>String: IsNullOrEmpty()
  SectionItemController->>image_url: Contains()
  SectionItemController->>ImageValidationUploadHelper: ValidateAndUploadAsync()
```

## Downstream
| Order | Target (BE-API / BE-INT / BE-EVT) | Sync/Async | Condition | Sent / used fields |
|---|---|---|---|---|
| — | none parsed beyond in-process services | — | — | — |

## Data touched
| Entity / table / SP | R/W | Notes |
|---|---|---|
| see service `data-model.md` | mixed | not fully attributed per action |

## Response (decrypted)
| Field (JSON) | Type | Always / when | Meaning |
|---|---|---|---|
| `success` | boolean | always | handler outcome |
| `responseCode` | string | always | mapped via CONFIG when handler used |
| `transactionStatus` | string | success | mapped message |
| `errorDescription` | string | failure | mapped or static |
| `appVersionInfo` | string | often | app version hint |
| `responseData` | object | success | action-specific |

Sample (synthetic):
```json
{
  "success": true,
  "responseCode": "<code>",
  "transactionStatus": "<message>",
  "appVersionInfo": "<version>",
  "responseData": {}
}
```

## Errors
| BE code | HTTP | ID | Condition | Message key/text | Retryable |
|---|---|---|---|---|---|
| 500 | 500 | BE-ERR-CONFIG-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-CONFIG-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-CONFIG-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SectionItemController.cs › SectionItemController.SaveSectionItemAsync` @ `9c00072`
- Decrypted DTO `SectionItemDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
