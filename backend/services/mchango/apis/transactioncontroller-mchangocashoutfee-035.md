---
kb_section: backend
type: api-contract
ids: [BE-API-MCHANGO-035]
service: MCHANGO
repo: TZ-Tigo-SuperApp-MChango
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 7c288ab
updated: 2026-10-05
confidence: confirmed
---

# BE-API-MCHANGO-035 TransactionController.MchangoCashoutFee
**Service:** BE-SVC-MCHANGO · **Handler:** `TZ-Tigo-SuperApp-MChango/TZTigoMChangoService/Controllers/MobileControllers/TransactionController.cs › TransactionController.MchangoCashoutFee` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/mobile/Transaction/MchangoCashoutFee
  internal_path: /api/mobile/Transaction/MchangoCashoutFee
  dispatch_field: null
  dispatch_value: null
  controller_action: TransactionController.MchangoCashoutFee
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/mobile/Transaction/MchangoCashoutFee`
- **Auth / filters:** none on action (pipeline may still authorize)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `Method` | `RefType` | N | — | shape only | Method |
| `requestingOrganisationTransactionReference` | `string?` | N | — | shape only | requestingOrganisationTransactionReference |
| `useCaseName` | `string?` | N | — | shape only | useCaseName |
| `isMerchant` | `bool` | N | — | shape only | isMerchant |
| `pushUpdateStatus` | `bool` | N | — | shape only | pushUpdateStatus |
| `ipInfo` | `string?` | N | — | shape only | ipInfo |
| `channel` | `string?` | N | — | shape only | channel |
| `appVersion` | `string?` | N | — | shape only | appVersion |
| `languageCode` | `string?` | N | — | shape only | languageCode |
| `deviceId` | `string?` | N | — | shape only | deviceId |
| `deviceMaker` | `string?` | N | — | shape only | deviceMaker |
| `deviceType` | `string?` | N | — | shape only | deviceType |
| `OS` | `string?` | N | — | shape only | OS |
| `pushId` | `string?` | N | — | shape only | pushId |
| `latitude` | `string?` | N | — | shape only | latitude |
| `longitude` | `string?` | N | — | shape only | longitude |
| `msisdn` | `string?` | N | — | shape only | msisdn |
| `Amount` | `float` | N | — | shape only | Amount |
| `SegmentType` | `string?` | N | — | shape only | SegmentType |
| `TargetMSISDN` | `string?` | N | — | shape only | TargetMSISDN |
| `PINCode` | `string?` | N | — | shape only | PINCode |

Headers / route / query params: none parsed beyond action signature `[('request', 'MchangoCashoutFeeDto')]`

Sample (synthetic):
```json
{
  "Method": "<string>",
  "requestingOrganisationTransactionReference": "<string>",
  "useCaseName": "<string>",
  "isMerchant": false,
  "pushUpdateStatus": false,
  "ipInfo": "<encrypted-pin>",
  "channel": "<string>",
  "appVersion": "<string>",
  "languageCode": "<string>",
  "deviceId": "<device-id>",
  "deviceMaker": "<string>",
  "deviceType": "<string>",
  "OS": "<string>",
  "pushId": "<push-token>",
  "latitude": "<lat>",
  "longitude": "<lng>",
  "msisdn": "255XXXXXXXXX",
  "Amount": "<amount>",
  "SegmentType": "<string>",
  "TargetMSISDN": "255XXXXXXXXX",
  "PINCode": "<encrypted-pin>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | No explicit guard parsed in action body | — | — | static parse |

## Internal call chain
1. Client POST `/api/mobile/Transaction/MchangoCashoutFee`.
2. `TransactionController.MchangoCashoutFee` runs (`TZ-Tigo-SuperApp-MChango/TZTigoMChangoService/Controllers/MobileControllers/TransactionController.cs`).
3. Calls `_transactionService.MchangoCashoutFee`.
4. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>TransactionController: POST /api/mobile/Transaction/MchangoCashoutFee
  participant TransactionController
  TransactionController->>_transactionService: MchangoCashoutFee()
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
| 500 | 500 | BE-ERR-MCHANGO-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-MCHANGO-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-MCHANGO-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-MChango/TZTigoMChangoService/Controllers/MobileControllers/TransactionController.cs › TransactionController.MchangoCashoutFee` @ `7c288ab`
- Decrypted DTO `MchangoCashoutFeeDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
