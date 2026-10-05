---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-028]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-028 MixxTipController.GetAllMerchants
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MixxTipController.cs › MixxTipController.GetAllMerchants` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/MixxTip/merchant/getall
  internal_path: /api/MixxTip/merchant/getall
  dispatch_field: null
  dispatch_value: null
  controller_action: MixxTipController.GetAllMerchants
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/MixxTip/merchant/getall`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `merchantcode` | `string?` | N | — | shape only | merchantcode |
| `search` | `string?` | N | — | shape only | search |
| `pageNumber` | `int` | N | — | shape only | pageNumber |
| `pageSize` | `int` | N | — | shape only | pageSize |

Headers / route / query params: none parsed beyond action signature `[('request', 'MixxTipMerchantListRequest')]`

Sample (synthetic):
```json
{
  "merchantcode": "<string>",
  "search": "<string>",
  "pageNumber": 0,
  "pageSize": 0
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `request.pageNumber <= 0` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MixxTipController.cs › MixxTipController.GetAllMerchants` |
| 2 | `request.pageSize <= 0 \|\| request.pageSize > 500` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MixxTipController.cs › MixxTipController.GetAllMerchants` |
| 3 | `!string.IsNullOrWhiteSpace(request.merchantcode` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MixxTipController.cs › MixxTipController.GetAllMerchants` |
| 4 | `!string.IsNullOrWhiteSpace(request.search` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MixxTipController.cs › MixxTipController.GetAllMerchants` |

## Internal call chain
1. Client POST `/api/MixxTip/merchant/getall`.
2. `MixxTipController.GetAllMerchants` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MixxTipController.cs`).
3. Calls `_repo.GetAllMerchantsAsync`.
4. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>MixxTipController: POST /api/MixxTip/merchant/getall
  participant MixxTipController
  MixxTipController->>_repo: GetAllMerchantsAsync()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MixxTipController.cs › MixxTipController.GetAllMerchants` @ `9c00072`
- Decrypted DTO `MixxTipMerchantListRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
