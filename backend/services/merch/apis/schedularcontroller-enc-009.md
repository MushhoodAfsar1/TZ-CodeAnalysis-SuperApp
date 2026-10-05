---
kb_section: backend
type: api-contract
ids: [BE-API-MERCH-009]
service: MERCH
repo: TZ-Tigo-SuperApp-Merchant
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 2367767
updated: 2026-10-05
confidence: confirmed
---

# BE-API-MERCH-009 SchedularController.enc
**Service:** BE-SVC-MERCH · **Handler:** `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/SchedularController.cs › SchedularController.enc` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Schedular/enc
  internal_path: /api/Schedular/enc
  dispatch_field: null
  dispatch_value: null
  controller_action: SchedularController.enc
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Schedular/enc`
- **Auth / filters:** none on action (pipeline may still authorize)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `requestingOrganisationTransactionReference` | `string?` | N | — | shape only | requestingOrganisationTransactionReference |
| `requestId` | `string?` | N | — | shape only | requestId |
| `channel` | `string?` | N | — | shape only | channel |
| `ipInfo` | `string?` | N | — | shape only | ipInfo |
| `appVersion` | `string?` | N | — | shape only | appVersion |
| `languageCode` | `string?` | N | — | shape only | languageCode |
| `deviceId` | `string?` | N | — | shape only | deviceId |
| `deviceMaker` | `string?` | N | — | shape only | deviceMaker |
| `oS` | `string?` | N | — | shape only | oS |
| `geoCode` | `string?` | N | — | shape only | geoCode |
| `userCaseName` | `string?` | N | — | shape only | userCaseName |
| `accessToken` | `string?` | N | — | shape only | accessToken |
| `pushId` | `string?` | N | — | shape only | pushId |
| `deviceType` | `string?` | N | — | shape only | deviceType |
| `Id` | `int` | N | — | shape only | Id |
| `Scheduler_Id` | `int?` | N | — | shape only | Scheduler_Id |
| `PIN` | `string?` | N | — | shape only | PIN |
| `MSISDN` | `string?` | N | max 50 | shape only | MSISDN |
| `ReceiverMSISDN` | `string?` | N | max 50 | shape only | ReceiverMSISDN |
| `AccountType` | `string?` | N | — | shape only | AccountType |
| `PaymentOption` | `PaymentOption?` | N | — | shape only | PaymentOption |
| `Amount` | `string?` | N | — | shape only | Amount |
| `BankId` | `string?` | N | max 50 | shape only | BankId |
| `shortCode` | `string?` | N | — | shape only | shortCode |
| `targetRefNumber` | `string?` | N | — | shape only | targetRefNumber |
| `PaymentType` | `string?` | N | — | shape only | PaymentType |
| `ChannelUser` | `string?` | N | — | shape only | ChannelUser |
| `ChannelPass` | `string?` | N | — | shape only | ChannelPass |
| `PaymentPercentage` | `string?` | N | — | shape only | PaymentPercentage |
| `ScheduleType` | `ScheduleType` | Y | — | [Required] | ScheduleType |
| `ScheduleValue` | `float` | Y | — | [Required] | ScheduleValue |
| `IsActive` | `bool?` | N | — | shape only | IsActive |
| `NextExecutionTime` | `DateTime?` | N | — | shape only | NextExecutionTime |
| `ScheduleTime` | `string?` | N | — | shape only | ScheduleTime |
| `IsUtilized` | `bool` | N | — | shape only | IsUtilized |
| `ThreadID` | `string?` | N | — | shape only | ThreadID |
| `UtilizationDateTime` | `DateTime?` | N | — | shape only | UtilizationDateTime |
| `CreatedBy` | `string?` | Y | — | [Required] | CreatedBy |
| `CreatedDate` | `DateTime` | Y | — | [Required] | CreatedDate |
| `ModifiedBy` | `string?` | N | — | shape only | ModifiedBy |
| `ModifiedDate` | `DateTime?` | N | — | shape only | ModifiedDate |
| `IsDeleted` | `bool` | N | — | shape only | IsDeleted |
| `requestingOrganisationTransactionReference` | `string?` | N | — | shape only | requestingOrganisationTransactionReference |

Headers / route / query params: none parsed beyond action signature `[('mod', 'TransferScheduleRequest')]`

Sample (synthetic):
```json
{
  "requestingOrganisationTransactionReference": "<string>",
  "requestId": "<string>",
  "channel": "<string>",
  "ipInfo": "<encrypted-pin>",
  "appVersion": "<string>",
  "languageCode": "<string>",
  "deviceId": "<device-id>",
  "deviceMaker": "<string>",
  "oS": "<string>",
  "geoCode": "<string>",
  "userCaseName": "<string>",
  "accessToken": "<jwt>",
  "pushId": "<push-token>",
  "deviceType": "<string>",
  "Id": 0,
  "Scheduler_Id": 0,
  "PIN": "<encrypted-pin>",
  "MSISDN": "255XXXXXXXXX",
  "ReceiverMSISDN": "255XXXXXXXXX",
  "AccountType": "<string>",
  "PaymentOption": "<string>",
  "Amount": "<amount>",
  "BankId": "<string>",
  "shortCode": "<string>",
  "targetRefNumber": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | No explicit guard parsed in action body | — | — | static parse |

## Internal call chain
1. Client POST `/api/Schedular/enc`.
2. `SchedularController.enc` runs (`TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/SchedularController.cs`).
3. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>SchedularController: POST /api/Schedular/enc
  participant SchedularController
  SchedularController->>App: envelope
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
- `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/SchedularController.cs › SchedularController.enc` @ `2367767`
- Decrypted DTO `TransferScheduleRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
