---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-321]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-321 FaqController.Create
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/FaqController.cs › FaqController.Create` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Faq/create
  internal_path: /api/Faq/create
  dispatch_field: null
  dispatch_value: null
  controller_action: FaqController.Create
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Faq/create`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `Id` | `int` | N | — | shape only | Id |
| `section_id` | `int?` | N | — | shape only | section_id |
| `section_item_id` | `int?` | N | — | shape only | section_item_id |
| `sub_section_item_id` | `int?` | N | — | shape only | sub_section_item_id |
| `question` | `string?` | N | — | shape only | question |
| `answer` | `string?` | N | — | shape only | answer |
| `status` | `bool?` | N | — | shape only | status |
| `deleted` | `bool?` | N | — | shape only | deleted |
| `created_by` | `string?` | N | — | shape only | created_by |
| `created_date` | `DateTime?` | N | — | shape only | created_date |
| `updated_by` | `string?` | N | — | shape only | updated_by |
| `updated_date` | `DateTime?` | N | — | shape only | updated_date |
| `faq_Translations` | `List<FaqTranslationsRequest>?` | N | — | shape only | faq_Translations |
| `country_id` | `int?` | N | — | shape only | country_id |
| `channel_id` | `int?` | N | — | shape only | channel_id |
| `os_id` | `int?` | N | — | shape only | os_id |

Headers / route / query params: none parsed beyond action signature `[('faq', 'FaqRequest')]`

Sample (synthetic):
```json
{
  "Id": 0,
  "section_id": 0,
  "section_item_id": 0,
  "sub_section_item_id": 0,
  "question": "<string>",
  "answer": "<string>",
  "status": false,
  "deleted": false,
  "created_by": "<string>",
  "created_date": "<iso-datetime>",
  "updated_by": "<string>",
  "updated_date": "<iso-datetime>",
  "faq_Translations": [],
  "country_id": 0,
  "channel_id": 0,
  "os_id": 0
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/FaqController.cs › FaqController.Create` |
| 2 | `imageSubCategoriesList != null && imageSubCategoriesList.Data != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/FaqController.cs › FaqController.Create` |
| 3 | `subCategoryId != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/FaqController.cs › FaqController.Create` |
| 4 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/FaqController.cs › FaqController.Create` |
| 5 | `_configuration.GetValue<string>("EnableLog:Error"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/FaqController.cs › FaqController.Create` |

## Internal call chain
1. Client POST `/api/Faq/create`.
2. `FaqController.Create` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/FaqController.cs`).
3. Calls `_logger.LogDebug`.
4. Calls `MethodBase.GetCurrentMethod`.
5. Calls `MethodBase.GetCurrentMethod`.
6. Calls `Diagnostics.StackFrame`.
7. Calls `User.FindFirst`.
8. Calls `Utilities.GetDateTime`.
9. Calls `_faqRepository.CreateAsync`.
10. Calls `_logger.LogDebug`.
11. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>FaqController: POST /api/Faq/create
  participant FaqController
  FaqController->>_logger: LogDebug()
  FaqController->>MethodBase: GetCurrentMethod()
  FaqController->>faq: ToString()
  FaqController->>Diagnostics: StackFrame()
  FaqController->>User: FindFirst()
  FaqController->>Value: ToString()
  FaqController->>Utilities: GetDateTime()
  FaqController->>_faqRepository: CreateAsync()
  FaqController->>faqmod: ToString()
  FaqController->>_logger: LogError()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/FaqController.cs › FaqController.Create` @ `9c00072`
- Decrypted DTO `FaqRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
