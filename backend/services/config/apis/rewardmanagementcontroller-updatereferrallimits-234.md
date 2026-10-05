---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-234]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-234 RewardManagementController.UpdateReferralLimits
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/RewardManagementController.cs › RewardManagementController.UpdateReferralLimits` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/RewardManagement/updatereferrallimits
  internal_path: /api/RewardManagement/updatereferrallimits
  dispatch_field: null
  dispatch_value: null
  controller_action: RewardManagementController.UpdateReferralLimits
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/RewardManagement/updatereferrallimits`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `id` | `int` | N | — | shape only | id |
| `dailyLimit` | `int` | N | — | shape only | dailyLimit |
| `weeklyLimit` | `int` | N | — | shape only | weeklyLimit |
| `monthlyLimit` | `int` | N | — | shape only | monthlyLimit |
| `yearlyLimit` | `int` | N | — | shape only | yearlyLimit |
| `isActive` | `bool` | N | — | shape only | isActive |

Headers / route / query params: none parsed beyond action signature `[('referralLimitsDto', 'ReferralLimitsDto')]`

Sample (synthetic):
```json
{
  "id": 0,
  "dailyLimit": 0,
  "weeklyLimit": 0,
  "monthlyLimit": 0,
  "yearlyLimit": 0,
  "isActive": false
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `response.success == false` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/RewardManagementController.cs › RewardManagementController.UpdateReferralLimits` |
| 2 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/RewardManagementController.cs › RewardManagementController.UpdateReferralLimits` |
| 3 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/RewardManagementController.cs › RewardManagementController.UpdateReferralLimits` |
| 4 | `_configuration.GetValue<string>("EnableLog:Error"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/RewardManagementController.cs › RewardManagementController.UpdateReferralLimits` |

## Internal call chain
1. Client POST `/api/RewardManagement/updatereferrallimits`.
2. `RewardManagementController.UpdateReferralLimits` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/RewardManagementController.cs`).
3. Calls `_logger.LogDebug`.
4. Calls `MethodBase.GetCurrentMethod`.
5. Calls `MethodBase.GetCurrentMethod`.
6. Calls `JsonConvert.SerializeObject`.
7. Calls `Diagnostics.StackFrame`.
8. Calls `_rewardManagementService.UpdateReferralLimitsAsync`.
9. Calls `_logger.LogDebug`.
10. Calls `MethodBase.GetCurrentMethod`.
11. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>RewardManagementController: POST /api/RewardManagement/updatereferrallimits
  participant RewardManagementController
  RewardManagementController->>_logger: LogDebug()
  RewardManagementController->>MethodBase: GetCurrentMethod()
  RewardManagementController->>Diagnostics: StackFrame()
  RewardManagementController->>_rewardManagementService: UpdateReferralLimitsAsync()
  RewardManagementController->>_logger: LogError()
  RewardManagementController->>ex: ToString()
  RewardManagementController->>Message: ToString()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/RewardManagementController.cs › RewardManagementController.UpdateReferralLimits` @ `9c00072`
- Decrypted DTO `ReferralLimitsDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
