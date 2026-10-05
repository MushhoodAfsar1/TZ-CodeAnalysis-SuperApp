---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-303]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-303 BankBillersController.ImportBanksBillers
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.ImportBanksBillers` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/BankBillers/importbanksbillers
  internal_path: /api/BankBillers/importbanksbillers
  dispatch_field: null
  dispatch_value: null
  controller_action: BankBillersController.ImportBanksBillers
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/BankBillers/importbanksbillers`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `Id` | `int` | N | — | shape only | Id |
| `File` | `string?` | N | — | shape only | File |
| `FileLocation` | `string?` | N | — | shape only | FileLocation |
| `FileName` | `string?` | N | — | shape only | FileName |
| `FileSize` | `string?` | N | — | shape only | FileSize |
| `OperatorType` | `string?` | N | — | shape only | OperatorType |

Headers / route / query params: none parsed beyond action signature `[('banksBillersFile', 'FileTransfer')]`

Sample (synthetic):
```json
{
  "Id": 0,
  "File": "<string>",
  "FileLocation": "<string>",
  "FileName": "<string>",
  "FileSize": "<string>",
  "OperatorType": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `!file.FileName.EndsWith(".csv"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.ImportBanksBillers` |
| 2 | `response.success == false` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.ImportBanksBillers` |
| 3 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.ImportBanksBillers` |
| 4 | `operatorType == "Bank"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.ImportBanksBillers` |
| 5 | `j > 0` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.ImportBanksBillers` |
| 6 | `s != ""` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.ImportBanksBillers` |
| 7 | `operatorType == "Biller"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.ImportBanksBillers` |
| 8 | `j > 0` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.ImportBanksBillers` |
| 9 | `s != ""` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.ImportBanksBillers` |
| 10 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.ImportBanksBillers` |

## Internal call chain
1. Client POST `/api/BankBillers/importbanksbillers`.
2. `BankBillersController.ImportBanksBillers` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs`).
3. Calls `FileHelper.Base64ToFile`.
4. Calls `FileName.EndsWith`.
5. Calls `ModelState.AddModelError`.
6. Calls `this.StatusCode`.
7. Calls `_logger.LogDebug`.
8. Calls `MethodBase.GetCurrentMethod`.
9. Calls `MethodBase.GetCurrentMethod`.
10. Calls `Diagnostics.StackFrame`.
11. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>BankBillersController: POST /api/BankBillers/importbanksbillers
  participant BankBillersController
  BankBillersController->>FileHelper: Base64ToFile()
  BankBillersController->>FileName: EndsWith()
  BankBillersController->>ModelState: AddModelError()
  BankBillersController->>_logger: LogDebug()
  BankBillersController->>MethodBase: GetCurrentMethod()
  BankBillersController->>Diagnostics: StackFrame()
  BankBillersController->>_bankBillersService: ImportBankBillersAsync()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/BankBillersController.cs › BankBillersController.ImportBanksBillers` @ `9c00072`
- Decrypted DTO `FileTransfer` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
