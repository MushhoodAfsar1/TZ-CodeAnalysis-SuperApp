---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-150]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-150 LeaderboardController.ImportWinners
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/LeaderboardController.cs › LeaderboardController.ImportWinners` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Leaderboard/winners/importfile
  internal_path: /api/Leaderboard/winners/importfile
  dispatch_field: null
  dispatch_value: null
  controller_action: LeaderboardController.ImportWinners
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Leaderboard/winners/importfile`
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
| `period_type` | `string?` | N | — | shape only | period_type |

Headers / route / query params: none parsed beyond action signature `[('request', 'LeaderboardWinnerImportRequest')]`

Sample (synthetic):
```json
{
  "Id": 0,
  "File": "<string>",
  "FileLocation": "<string>",
  "FileName": "<string>",
  "FileSize": "<string>",
  "OperatorType": "<string>",
  "period_type": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `request == null \|\| string.IsNullOrWhiteSpace(request.File` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/LeaderboardController.cs › LeaderboardController.ImportWinners` |
| 2 | `!IsCsvOrExcelFileName(request.FileName` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/LeaderboardController.cs › LeaderboardController.ImportWinners` |
| 3 | `file == null \|\| file.Length == 0` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/LeaderboardController.cs › LeaderboardController.ImportWinners` |
| 4 | `!response.success` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/LeaderboardController.cs › LeaderboardController.ImportWinners` |
| 5 | `string.IsNullOrEmpty(period` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/LeaderboardController.cs › LeaderboardController.ImportWinners` |
| 6 | `parsed.Count == 0` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/LeaderboardController.cs › LeaderboardController.ImportWinners` |
| 7 | `existing.Count > 0` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/LeaderboardController.cs › LeaderboardController.ImportWinners` |
| 8 | `_configuration.GetValue<string>("EnableLog:Error"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/LeaderboardController.cs › LeaderboardController.ImportWinners` |

## Internal call chain
1. Client POST `/api/Leaderboard/winners/importfile`.
2. `LeaderboardController.ImportWinners` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/LeaderboardController.cs`).
3. Calls `string.IsNullOrWhiteSpace`.
4. Calls `_repo.ImportWinnersAsync`.
5. Calls `MethodBase.GetCurrentMethod`.
6. Calls `MethodBase.GetCurrentMethod`.
7. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>LeaderboardController: POST /api/Leaderboard/winners/importfile
  participant LeaderboardController
  LeaderboardController->>string: IsNullOrWhiteSpace()
  LeaderboardController->>_repo: ImportWinnersAsync()
  LeaderboardController->>_logger: LogError()
  LeaderboardController->>MethodBase: GetCurrentMethod()
  LeaderboardController->>ex: ToString()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/LeaderboardController.cs › LeaderboardController.ImportWinners` @ `9c00072`
- Decrypted DTO `LeaderboardWinnerImportRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
