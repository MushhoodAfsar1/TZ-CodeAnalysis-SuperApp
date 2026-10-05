---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-333]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-333 FooterController.Update
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/FooterController.cs › FooterController.Update` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Footer/update
  internal_path: /api/Footer/update
  dispatch_field: null
  dispatch_value: null
  controller_action: FooterController.Update
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Footer/update`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `Id` | `int` | N | — | shape only | Id |
| `title` | `string` | N | — | shape only | title |
| `title_sw` | `string?` | N | — | shape only | title_sw |
| `flow_id` | `string?` | N | — | shape only | flow_id |
| `icon_light` | `string?` | N | — | shape only | icon_light |
| `icon_dark` | `string?` | N | — | shape only | icon_dark |
| `enabled` | `bool` | N | — | shape only | enabled |
| `sort_order` | `int` | N | — | shape only | sort_order |
| `created_by` | `string?` | N | — | shape only | created_by |
| `created_date` | `DateTime?` | N | — | shape only | created_date |
| `updated_by` | `string?` | N | — | shape only | updated_by |
| `updated_date` | `DateTime?` | N | — | shape only | updated_date |

Headers / route / query params: none parsed beyond action signature `[('dto', 'FooterDto')]`

Sample (synthetic):
```json
{
  "Id": 0,
  "title": "<string>",
  "title_sw": "<string>",
  "flow_id": "<string>",
  "icon_light": "<string>",
  "icon_dark": "<string>",
  "enabled": false,
  "sort_order": 0,
  "created_by": "<string>",
  "created_date": "<iso-datetime>",
  "updated_by": "<string>",
  "updated_date": "<iso-datetime>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `dto.Id <= 0` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/FooterController.cs › FooterController.Update` |
| 2 | `existing == null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/FooterController.cs › FooterController.Update` |
| 3 | `string.IsNullOrWhiteSpace(dto.title` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/FooterController.cs › FooterController.Update` |
| 4 | `!string.IsNullOrEmpty(dto.icon_light` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/FooterController.cs › FooterController.Update` |
| 5 | `dto.icon_light.Equals("REMOVE", StringComparison.OrdinalIgnoreCase` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/FooterController.cs › FooterController.Update` |
| 6 | `dto.icon_light.Contains("base64"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/FooterController.cs › FooterController.Update` |

## Internal call chain
1. Client POST `/api/Footer/update`.
2. `FooterController.Update` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/FooterController.cs`).
3. Calls `_repository.GetByIdAsync`.
4. Calls `string.IsNullOrWhiteSpace`.
5. Calls `string.IsNullOrEmpty`.
6. Calls `icon_light.Equals`.
7. Calls `icon_light.Contains`.
8. Calls `ImageUploadHelper.Upload`.
9. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>FooterController: POST /api/Footer/update
  participant FooterController
  FooterController->>_repository: GetByIdAsync()
  FooterController->>string: IsNullOrWhiteSpace()
  FooterController->>string: IsNullOrEmpty()
  FooterController->>icon_light: Equals()
  FooterController->>icon_light: Contains()
  FooterController->>ImageUploadHelper: Upload()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/FooterController.cs › FooterController.Update` @ `9c00072`
- Decrypted DTO `FooterDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
