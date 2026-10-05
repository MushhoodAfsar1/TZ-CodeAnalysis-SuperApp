---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-114]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-114 SubSectionItemController.SaveSubSectionItemAsync
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SubSectionItemController.cs › SubSectionItemController.SaveSubSectionItemAsync` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/SubSectionItem/update
  internal_path: /api/SubSectionItem/update
  dispatch_field: null
  dispatch_value: null
  controller_action: SubSectionItemController.SaveSubSectionItemAsync
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/SubSectionItem/update`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `Id` | `Int32` | N | — | shape only | Id |
| `section_item_id` | `Int32` | N | — | shape only | section_item_id |
| `name` | `string` | N | — | shape only | name |
| `ussdCode` | `string?` | N | — | shape only | ussdCode |
| `shortCode` | `string?` | N | — | shape only | shortCode |
| `code` | `string?` | N | — | shape only | code |
| `merchantShortCode` | `string?` | N | — | shape only | merchantShortCode |
| `segment1` | `string?` | N | — | shape only | segment1 |
| `segment2` | `string?` | N | — | shape only | segment2 |
| `segment3` | `string?` | N | — | shape only | segment3 |
| `segment4` | `string?` | N | — | shape only | segment4 |
| `image_url` | `string` | N | — | shape only | image_url |
| `dark_image_url` | `string` | N | — | shape only | dark_image_url |
| `sort_order` | `Int32` | N | — | shape only | sort_order |
| `newly_added` | `Int32` | N | — | shape only | newly_added |
| `description` | `string` | N | — | shape only | description |
| `created_by` | `string` | N | — | shape only | created_by |
| `created_date` | `DateTime` | N | — | shape only | created_date |
| `updated_by` | `string` | N | — | shape only | updated_by |
| `updated_date` | `DateTime` | N | — | shape only | updated_date |
| `version_android` | `string` | N | — | shape only | version_android |
| `version_ios` | `string` | N | — | shape only | version_ios |
| `messages` | `List<DashboardMultilingualMessage>` | N | — | shape only | messages |
| `country_id` | `Int32` | N | — | shape only | country_id |
| `channel_id` | `Int32` | N | — | shape only | channel_id |
| `app_version_id` | `Int32` | N | — | shape only | app_version_id |
| `flow_id` | `string` | N | — | shape only | flow_id |
| `standardPrice` | `string?` | N | — | shape only | standardPrice |
| `xtraViewPvrPrice` | `string?` | N | — | shape only | xtraViewPvrPrice |
| `countryCode` | `string?` | N | — | shape only | countryCode |
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
| `url` | `string?` | N | — | shape only | url |
| `time_check` | `Boolean?` | N | — | shape only | time_check |
| `isactive` | `Boolean?` | N | — | shape only | isactive |
| `isallowquickaction` | `Boolean` | N | — | shape only | isallowquickaction |
| `is_merchant_biller` | `Boolean` | N | — | shape only | is_merchant_biller |

Headers / route / query params: none parsed beyond action signature `[('sub_section_item_dto', 'SubSectionItemDto')]`

Sample (synthetic):
```json
{
  "Id": 0,
  "section_item_id": 0,
  "name": "<string>",
  "ussdCode": "<string>",
  "shortCode": "<string>",
  "code": "<string>",
  "merchantShortCode": "<string>",
  "segment1": "<string>",
  "segment2": "<string>",
  "segment3": "<string>",
  "segment4": "<string>",
  "image_url": "<string>",
  "dark_image_url": "<string>",
  "sort_order": 0,
  "newly_added": 0,
  "description": "<string>",
  "created_by": "<string>",
  "created_date": "<iso-datetime>",
  "updated_by": "<string>",
  "updated_date": "<iso-datetime>",
  "version_android": "<string>",
  "version_ios": "<string>",
  "messages": [],
  "country_id": 0,
  "channel_id": 0
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `(sub_section_item_db != null && sub_section_item_db.image_url != sub_section_item_dto.image_url` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SubSectionItemController.cs › SubSectionItemController.SaveSubSectionItemAsync` |
| 2 | `sub_section_item_dto.image_url != null && (sub_section_item_dto.image_url.Contains("data:image"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SubSectionItemController.cs › SubSectionItemController.SaveSubSectionItemAsync` |
| 3 | `!validationResult.IsValid` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SubSectionItemController.cs › SubSectionItemController.SaveSubSectionItemAsync` |
| 4 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SubSectionItemController.cs › SubSectionItemController.SaveSubSectionItemAsync` |

## Internal call chain
1. Client POST `/api/SubSectionItem/update`.
2. `SubSectionItemController.SaveSubSectionItemAsync` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SubSectionItemController.cs`).
3. Calls `_logger.LogDebug`.
4. Calls `MethodBase.GetCurrentMethod`.
5. Calls `MethodBase.GetCurrentMethod`.
6. Calls `Diagnostics.StackFrame`.
7. Calls `_subSectionItemRepository.GetById`.
8. Calls `String.IsNullOrEmpty`.
9. Calls `image_url.Contains`.
10. Calls `image_url.Contains`.
11. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>SubSectionItemController: POST /api/SubSectionItem/update
  participant SubSectionItemController
  SubSectionItemController->>_logger: LogDebug()
  SubSectionItemController->>MethodBase: GetCurrentMethod()
  SubSectionItemController->>sub_section_item_dto: ToString()
  SubSectionItemController->>Diagnostics: StackFrame()
  SubSectionItemController->>_subSectionItemRepository: GetById()
  SubSectionItemController->>String: IsNullOrEmpty()
  SubSectionItemController->>image_url: Contains()
  SubSectionItemController->>ImageValidationUploadHelper: ValidateAndUploadAsync()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/SubSectionItemController.cs › SubSectionItemController.SaveSubSectionItemAsync` @ `9c00072`
- Decrypted DTO `SubSectionItemDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
