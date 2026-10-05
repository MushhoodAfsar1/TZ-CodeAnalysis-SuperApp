---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-288]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-288 DeviceBlockingController.updateBlocking
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/DeviceBlockingController.cs › DeviceBlockingController.updateBlocking` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/DeviceBlocking/updateBlocking
  internal_path: /api/DeviceBlocking/updateBlocking
  dispatch_field: null
  dispatch_value: null
  controller_action: DeviceBlockingController.updateBlocking
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/DeviceBlocking/updateBlocking`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `Id` | `int` | N | — | shape only | Id |
| `blockingId` | `string?` | N | — | shape only | blockingId |
| `deviceName` | `string?` | N | — | shape only | deviceName |
| `blockingType` | `string?` | N | — | shape only | blockingType |
| `blockedDate` | `DateTime?` | N | — | shape only | blockedDate |
| `deviceStatus` | `string?` | N | — | shape only | deviceStatus |
| `description` | `string?` | N | — | shape only | description |
| `createdby` | `string?` | N | — | shape only | createdby |
| `updatedby` | `string?` | N | — | shape only | updatedby |
| `translationsMessages` | `List<TranslationsMessages>?` | N | — | shape only | translationsMessages |

Headers / route / query params: none parsed beyond action signature `[('request', 'Blocking')]`

Sample (synthetic):
```json
{
  "Id": 0,
  "blockingId": "<string>",
  "deviceName": "<string>",
  "blockingType": "<string>",
  "blockedDate": "<iso-datetime>",
  "deviceStatus": "<string>",
  "description": "<string>",
  "createdby": "<string>",
  "updatedby": "<string>",
  "translationsMessages": []
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `request != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/DeviceBlockingController.cs › DeviceBlockingController.updateBlocking` |
| 2 | `request.Id == 0 && request.blockingType == "Blocked"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/DeviceBlockingController.cs › DeviceBlockingController.updateBlocking` |
| 3 | `request.Id > 0` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/DeviceBlockingController.cs › DeviceBlockingController.updateBlocking` |
| 4 | `item == null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/DeviceBlockingController.cs › DeviceBlockingController.updateBlocking` |
| 5 | `msg.message != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/DeviceBlockingController.cs › DeviceBlockingController.updateBlocking` |

## Internal call chain
1. Client POST `/api/DeviceBlocking/updateBlocking`.
2. `DeviceBlockingController.updateBlocking` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/DeviceBlockingController.cs`).
3. Calls `User.FindFirst`.
4. Calls `User.FindFirst`.
5. Calls `_deviceBlockingRepository.updateBlocking`.
6. Calls `this.StatusCode`.
7. Calls `this.StatusCode`.
8. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>DeviceBlockingController: POST /api/DeviceBlocking/updateBlocking
  participant DeviceBlockingController
  DeviceBlockingController->>User: FindFirst()
  DeviceBlockingController->>Value: ToString()
  DeviceBlockingController->>_deviceBlockingRepository: updateBlocking()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/DeviceBlockingController.cs › DeviceBlockingController.updateBlocking` @ `9c00072`
- Decrypted DTO `Blocking` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
