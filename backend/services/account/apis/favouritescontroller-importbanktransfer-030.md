---
kb_section: backend
type: api-contract
ids: [BE-API-ACCOUNT-030]
service: ACCOUNT
repo: TZ-Tigo-SuperApp-Account
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 5c549d6
updated: 2026-10-05
confidence: confirmed
---

# BE-API-ACCOUNT-030 FavouritesController.ImportBankTransfer
**Service:** BE-SVC-ACCOUNT · **Handler:** `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.ImportBankTransfer` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Favourites/importcsvbanktransfer
  internal_path: /api/Favourites/importcsvbanktransfer
  dispatch_field: null
  dispatch_value: null
  controller_action: FavouritesController.ImportBankTransfer
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Favourites/importcsvbanktransfer`
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
| 1 | `!file.FileName.EndsWith(".csv"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.ImportBankTransfer` |
| 2 | `response.success == false` | branch / error envelope | — | `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.ImportBankTransfer` |
| 3 | `operatorType == "Data Bundle"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.ImportBankTransfer` |
| 4 | `j == 0` | branch / error envelope | — | `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.ImportBankTransfer` |
| 5 | `j > 0 && fields.Length == expectedColumnCount` | branch / error envelope | — | `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.ImportBankTransfer` |
| 6 | `favourites.Any(` | branch / error envelope | — | `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.ImportBankTransfer` |

## Internal call chain
1. Client POST `/api/Favourites/importcsvbanktransfer`.
2. `FavouritesController.ImportBankTransfer` runs (`TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs`).
3. Calls `FileName.EndsWith`.
4. Calls `ModelState.AddModelError`.
5. Calls `this.StatusCode`.
6. Calls `_favouritesService.ImportFavouritesBankTransferAsync`.
7. Calls `this.StatusCode`.
8. Calls `this.StatusCode`.
9. Calls `this.StatusCode`.
10. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>FavouritesController: POST /api/Favourites/importcsvbanktransfer
  participant FavouritesController
  FavouritesController->>FileName: EndsWith()
  FavouritesController->>ModelState: AddModelError()
  FavouritesController->>_favouritesService: ImportFavouritesBankTransferAsync()
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
| 500 | 500 | BE-ERR-ACCOUNT-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-ACCOUNT-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-ACCOUNT-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/FavouritesController.cs › FavouritesController.ImportBankTransfer` @ `5c549d6`

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
