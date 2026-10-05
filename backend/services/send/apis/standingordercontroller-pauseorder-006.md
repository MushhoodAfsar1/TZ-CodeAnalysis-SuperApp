---
kb_section: backend
type: api-contract
ids: [BE-API-SEND-006]
service: SEND
repo: TZ-Tigo-SuperApp-SendMoney
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 599771b
updated: 2026-10-05
confidence: confirmed
---

# BE-API-SEND-006 StandingOrderController.PauseOrder
**Service:** BE-SVC-SEND · **Handler:** `TZ-Tigo-SuperApp-SendMoney/TZTigoSuperAppSendMoney/Controllers/StandingOrderController.cs › StandingOrderController.PauseOrder` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/StandingOrder/PauseOrder
  internal_path: /api/StandingOrder/PauseOrder
  dispatch_field: null
  dispatch_value: null
  controller_action: StandingOrderController.PauseOrder
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/StandingOrder/PauseOrder`
- **Auth / filters:** EncryptionProviderFilter<PauseOrderRequestDTO>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `PauseOrderRequestDTO`

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `requestingOrganisationTransactionReference` | `string?` | N | — | shape only | requestingOrganisationTransactionReference |
| `requestID` | `string?` | N | — | shape only | requestID |
| `channel` | `string?` | N | — | shape only | channel |
| `ipInfo` | `string?` | N | — | shape only | ipInfo |
| `appVersion` | `string?` | N | — | shape only | appVersion |
| `languageCode` | `string?` | N | — | shape only | languageCode |
| `deviceId` | `string?` | N | — | shape only | deviceId |
| `deviceMaker` | `string?` | N | — | shape only | deviceMaker |
| `oS` | `string?` | N | — | shape only | oS |
| `pushId` | `string?` | N | — | shape only | pushId |
| `deviceType` | `string?` | N | — | shape only | deviceType |
| `geoCode` | `string?` | N | — | shape only | geoCode |
| `userCaseName` | `string?` | N | — | shape only | userCaseName |
| `accessToken` | `string?` | N | — | shape only | accessToken |
| `qrType` | `string?` | N | — | shape only | qrType |
| `Order_Id` | `int?` | N | — | shape only | Order_Id |
| `Msisdn` | `string?` | N | — | shape only | Msisdn |

Headers / route / query params: none parsed beyond action signature `[('msg', 'RequestModel')]`

Sample (synthetic):
```json
{"payload": "<ciphertext-or-json>"}
# decrypted payload:
{
  "requestingOrganisationTransactionReference": "<string>",
  "requestID": "<string>",
  "channel": "<string>",
  "ipInfo": "<encrypted-pin>",
  "appVersion": "<string>",
  "languageCode": "<string>",
  "deviceId": "<device-id>",
  "deviceMaker": "<string>",
  "oS": "<string>",
  "pushId": "<push-token>",
  "deviceType": "<string>",
  "geoCode": "<string>",
  "userCaseName": "<string>",
  "accessToken": "<jwt>",
  "qrType": "<string>",
  "Order_Id": 0,
  "Msisdn": "255XXXXXXXXX"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt | 500 | — | `StandingOrderController.PauseOrder` |
| 2 | Require Order_Id + Msisdn; GetCustomerId | fail | — | `StandingOrderRepository.PauseOrder` |
| 3 | Load StandingOrders by OrderId (`isdeleted!=true`); ownership match MSISDN | 404/fail | — | same |
| 4 | reject already paused / deleted / expired / not active|failed | 400 | — | same |
| 5 | DB status then HTTP `PauseOrderApiUrl` | partner 200/400/404/401 | — | same |

## Internal call chain
1. Client POST `/api/StandingOrder/PauseOrder` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `PauseOrderRequestDTO` on `HttpContext.Items['modeldata']`.
3. `StandingOrderController.PauseOrder` runs (`TZ-Tigo-SuperApp-SendMoney/TZTigoSuperAppSendMoney/Controllers/StandingOrderController.cs`).
4. Calls `_standingOrder.PauseOrder`.
5. Calls `_apiResponseHandler.ResponseObject`.
6. Calls `int.Parse`.
7. Calls `_apiResponseHandler.CreateResponse`.
8. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  participant EncFilter
  App->>EncFilter: POST payload envelope
  EncFilter->>EncFilter: AES decrypt payload
  EncFilter->>StandingOrderController: Items['modeldata']
  participant StandingOrderController
  StandingOrderController->>_standingOrder: PauseOrder()
  StandingOrderController->>Code: ToString()
  StandingOrderController->>_apiResponseHandler: ResponseObject()
  StandingOrderController->>int: Parse()
  StandingOrderController->>_logger: LogError()
  StandingOrderController->>_apiResponseHandler: CreateResponse()
```

## Downstream
| Order | Target | Sync/Async | Condition | Sent / used fields |
|---|---|---|---|---|
| 1 | HTTP `PauseOrderApiUrl` (+ token/customer keys) | Sync | after local status | Order_Id, Msisdn |
| 2 | EF StandingOrders | W | always | pause/resume/soft-delete |

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
| 500 | 500 | BE-ERR-SEND-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-SEND-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-SEND-001` (when session filter present).

## Config keys
- `PauseOrderApiUrl`, `GetTokenApiUrl`, `StandingOrderApiKey`, `GetCustomerIdApiUrl`

## Evidence
- `TZ-Tigo-SuperApp-SendMoney/TZTigoSuperAppSendMoney/Controllers/StandingOrderController.cs › StandingOrderController.PauseOrder` @ `599771b`
- Decrypted DTO `PauseOrderRequestDTO` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
