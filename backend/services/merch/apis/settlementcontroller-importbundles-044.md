---
kb_section: backend
type: api-contract
ids: [BE-API-MERCH-044]
service: MERCH
repo: TZ-Tigo-SuperApp-Merchant
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 2367767
updated: 2026-10-05
confidence: confirmed
---

# BE-API-MERCH-044 SettlementController.ImportBundles
**Service:** BE-SVC-MERCH · **Handler:** `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/SettlementController.cs › SettlementController.ImportBundles` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Settlement/importcsv
  internal_path: /api/Settlement/importcsv
  dispatch_field: null
  dispatch_value: null
  controller_action: SettlementController.ImportBundles
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Settlement/importcsv`
- **Auth / filters:** none on action (pipeline may still authorize)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| *(none parsed)* | | | | | |

Headers / route / query params: none parsed beyond action signature `[('file', 'IFormFile')]`

Sample (synthetic):
```json
{}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `!file.FileName.EndsWith(".csv"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/SettlementController.cs › SettlementController.ImportBundles` |
| 2 | `response.success == false` | branch / error envelope | — | `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/SettlementController.cs › SettlementController.ImportBundles` |
| 3 | `operatorType == "Data Bundle"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/SettlementController.cs › SettlementController.ImportBundles` |
| 4 | `j == 0` | branch / error envelope | — | `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/SettlementController.cs › SettlementController.ImportBundles` |
| 5 | `j > 0 && fields.Length == expectedColumnCount` | branch / error envelope | — | `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/SettlementController.cs › SettlementController.ImportBundles` |
| 6 | `_configuration.GetValue<string>("EnableLog:Error"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/SettlementController.cs › SettlementController.ImportBundles` |
| 7 | `param is string` | branch / error envelope | — | `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/SettlementController.cs › SettlementController.ImportBundles` |

## Internal call chain
1. Client POST `/api/Settlement/importcsv`.
2. `SettlementController.ImportBundles` runs (`TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/SettlementController.cs`).
3. Calls `FileName.EndsWith`.
4. Calls `ModelState.AddModelError`.
5. Calls `this.StatusCode`.
6. Calls `_uploaderService.ImportBundlesAsync`.
7. Calls `this.StatusCode`.
8. Calls `this.StatusCode`.
9. Calls `this.StatusCode`.
10. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>SettlementController: POST /api/Settlement/importcsv
  participant SettlementController
  SettlementController->>FileName: EndsWith()
  SettlementController->>ModelState: AddModelError()
  SettlementController->>_uploaderService: ImportBundlesAsync()
  SettlementController->>_logger: LogError()
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
| 500 | 500 | BE-ERR-MERCH-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-MERCH-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-MERCH-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/SettlementController.cs › SettlementController.ImportBundles` @ `2367767`

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
