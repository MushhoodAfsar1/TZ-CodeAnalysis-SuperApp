---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-033]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-033 MixxTipController.UpdateConfig
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MixxTipController.cs › MixxTipController.UpdateConfig` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/MixxTip/config/update
  internal_path: /api/MixxTip/config/update
  dispatch_field: null
  dispatch_value: null
  controller_action: MixxTipController.UpdateConfig
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/MixxTip/config/update`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `id` | `int` | N | — | shape only | id |
| `mixxtipenable` | `bool` | N | — | shape only | mixxtipenable |
| `mixxtipbannerenable` | `bool` | N | — | shape only | mixxtipbannerenable |
| `mixxtipallmerchants` | `bool` | N | — | shape only | mixxtipallmerchants |
| `mixxtipamount` | `decimal` | N | — | shape only | mixxtipamount |
| `mixxtipsourceaccount` | `string?` | N | — | shape only | mixxtipsourceaccount |
| `mixxtipeligiblemerchants` | `List<string>` | N | — | shape only | mixxtipeligiblemerchants |
| `bannerimageurl` | `string?` | N | — | shape only | bannerimageurl |
| `bannerdarkimageurl` | `string?` | N | — | shape only | bannerdarkimageurl |
| `receiptbannerimageurl` | `string?` | N | — | shape only | receiptbannerimageurl |
| `bannerheight` | `decimal` | N | — | shape only | bannerheight |
| `receiptbannerheight` | `decimal` | N | — | shape only | receiptbannerheight |
| `createdby` | `string?` | N | — | shape only | createdby |
| `createddate` | `DateTime?` | N | — | shape only | createddate |
| `updatedby` | `string?` | N | — | shape only | updatedby |
| `updateddate` | `DateTime?` | N | — | shape only | updateddate |

Headers / route / query params: none parsed beyond action signature `[('dto', 'MixxTipConfigDto')]`

Sample (synthetic):
```json
{
  "id": 0,
  "mixxtipenable": false,
  "mixxtipbannerenable": false,
  "mixxtipallmerchants": false,
  "mixxtipamount": "<amount>",
  "mixxtipsourceaccount": "<string>",
  "mixxtipeligiblemerchants": [],
  "bannerimageurl": "<string>",
  "bannerdarkimageurl": "<string>",
  "receiptbannerimageurl": "<string>",
  "bannerheight": 0,
  "receiptbannerheight": 0,
  "createdby": "<string>",
  "createddate": "<iso-datetime>",
  "updatedby": "<string>",
  "updateddate": "<iso-datetime>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `dto == null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MixxTipController.cs › MixxTipController.UpdateConfig` |
| 2 | `dto.mixxtipamount < 0` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MixxTipController.cs › MixxTipController.UpdateConfig` |
| 3 | `heightError != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MixxTipController.cs › MixxTipController.UpdateConfig` |
| 4 | `receiptHeightError != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MixxTipController.cs › MixxTipController.UpdateConfig` |
| 5 | `isNew` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MixxTipController.cs › MixxTipController.UpdateConfig` |
| 6 | `!isNew` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MixxTipController.cs › MixxTipController.UpdateConfig` |

## Internal call chain
1. Client POST `/api/MixxTip/config/update`.
2. `MixxTipController.UpdateConfig` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MixxTipController.cs`).
3. Calls `_repo.UpsertConfigAsync`.
4. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>MixxTipController: POST /api/MixxTip/config/update
  participant MixxTipController
  MixxTipController->>_repo: UpsertConfigAsync()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MixxTipController.cs › MixxTipController.UpdateConfig` @ `9c00072`
- Decrypted DTO `MixxTipConfigDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
