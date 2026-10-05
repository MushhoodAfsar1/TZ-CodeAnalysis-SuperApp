---
kb_section: backend
type: api-contract
ids: [BE-API-SAVING-002]
service: SAVING
repo: TZ-Tigo-SuperApp-Saving
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 2ca8791
updated: 2026-10-05
confidence: confirmed
---

# BE-API-SAVING-002 SavingController.enc
**Service:** BE-SVC-SAVING · **Handler:** `TZ-Tigo-SuperApp-Saving/TZTigoSuperAppSaving/Controllers/SavingController.cs › SavingController.enc` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Saving/enc
  internal_path: /api/Saving/enc
  dispatch_field: null
  dispatch_value: null
  controller_action: SavingController.enc
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Saving/enc`
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
| `pushId` | `string?` | N | — | shape only | pushId |
| `deviceType` | `string?` | N | — | shape only | deviceType |
| `deviceId` | `string?` | N | — | shape only | deviceId |
| `deviceMaker` | `string?` | N | — | shape only | deviceMaker |
| `oS` | `string?` | N | — | shape only | oS |
| `geoCode` | `string?` | N | — | shape only | geoCode |
| `userCaseName` | `string?` | N | — | shape only | userCaseName |
| `accessToken` | `string?` | N | — | shape only | accessToken |
| `consumerID` | `string?` | N | — | shape only | consumerID |
| `referenceID` | `string?` | N | — | shape only | referenceID |
| `sourceMSISDN` | `string?` | N | — | shape only | sourceMSISDN |
| `terminalType` | `string?` | N | — | shape only | terminalType |
| `sourcePIN` | `string?` | N | — | shape only | sourcePIN |
| `accountID` | `string?` | N | — | shape only | accountID |
| `operation` | `string?` | N | — | shape only | operation |
| `amount` | `string?` | N | — | shape only | amount |

Headers / route / query params: none parsed beyond action signature `[('mod', 'SubscriptionRequest')]`

Sample (synthetic):
```json
{
  "requestingOrganisationTransactionReference": "<string>",
  "requestId": "<string>",
  "channel": "<string>",
  "ipInfo": "<encrypted-pin>",
  "appVersion": "<string>",
  "languageCode": "<string>",
  "pushId": "<push-token>",
  "deviceType": "<string>",
  "deviceId": "<device-id>",
  "deviceMaker": "<string>",
  "oS": "<string>",
  "geoCode": "<string>",
  "userCaseName": "<string>",
  "accessToken": "<jwt>",
  "consumerID": "<string>",
  "referenceID": "<string>",
  "sourceMSISDN": "255XXXXXXXXX",
  "terminalType": "<string>",
  "sourcePIN": "<encrypted-pin>",
  "accountID": "<string>",
  "operation": "<string>",
  "amount": "<amount>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | No explicit guard parsed in action body | — | — | static parse |

## Internal call chain
1. Client POST `/api/Saving/enc`.
2. `SavingController.enc` runs (`TZ-Tigo-SuperApp-Saving/TZTigoSuperAppSaving/Controllers/SavingController.cs`).
3. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>SavingController: POST /api/Saving/enc
  participant SavingController
  SavingController->>App: envelope
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
| 500 | 500 | BE-ERR-SAVING-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-SAVING-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-SAVING-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-Saving/TZTigoSuperAppSaving/Controllers/SavingController.cs › SavingController.enc` @ `2ca8791`
- Decrypted DTO `SubscriptionRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
