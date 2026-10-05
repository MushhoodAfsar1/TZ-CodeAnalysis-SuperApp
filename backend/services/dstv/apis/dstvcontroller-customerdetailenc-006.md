---
kb_section: backend
type: api-contract
ids: [BE-API-DSTV-006]
service: DSTV
repo: TZ-Tigo-SuperApp-DigitalSubscription
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: fd31aa1
updated: 2026-10-05
confidence: confirmed
---

# BE-API-DSTV-006 DSTVController.CustomerDetailenc
**Service:** BE-SVC-DSTV · **Handler:** `TZ-Tigo-SuperApp-DigitalSubscription/TZTigoSuperAppDigitalSubscription/Controllers/DSTVController.cs › DSTVController.CustomerDetailenc` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/DSTV/CustomerDetailenc
  internal_path: /api/DSTV/CustomerDetailenc
  dispatch_field: null
  dispatch_value: null
  controller_action: DSTVController.CustomerDetailenc
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/DSTV/CustomerDetailenc`
- **Auth / filters:** none on action (pipeline may still authorize)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `requestingOrganisationTransactionReference` | `string` | N | — | shape only | requestingOrganisationTransactionReference |
| `requestId` | `string` | N | — | shape only | requestId |
| `channel` | `string` | N | — | shape only | channel |
| `ipInfo` | `string` | N | — | shape only | ipInfo |
| `appVersion` | `string` | N | — | shape only | appVersion |
| `languageCode` | `string` | N | — | shape only | languageCode |
| `deviceId` | `string` | N | — | shape only | deviceId |
| `deviceMaker` | `string` | N | — | shape only | deviceMaker |
| `oS` | `string` | N | — | shape only | oS |
| `geoCode` | `string` | N | — | shape only | geoCode |
| `userCaseName` | `string` | N | — | shape only | userCaseName |
| `accessToken` | `string` | N | — | shape only | accessToken |
| `dataSource` | `string` | N | — | shape only | dataSource |
| `deviceNumber` | `string` | N | — | shape only | deviceNumber |
| `vendorCode` | `string` | N | — | shape only | vendorCode |
| `currencyCode` | `string` | N | — | shape only | currencyCode |
| `businessUnit` | `string` | N | — | shape only | businessUnit |

Headers / route / query params: none parsed beyond action signature `[('mod', 'CustomerDetailRequest')]`

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
  "dataSource": "<string>",
  "deviceNumber": "<string>",
  "vendorCode": "<string>",
  "currencyCode": "<string>",
  "businessUnit": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | No explicit guard parsed in action body | — | — | static parse |

## Internal call chain
1. Client POST `/api/DSTV/CustomerDetailenc`.
2. `DSTVController.CustomerDetailenc` runs (`TZ-Tigo-SuperApp-DigitalSubscription/TZTigoSuperAppDigitalSubscription/Controllers/DSTVController.cs`).
3. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>DSTVController: POST /api/DSTV/CustomerDetailenc
  participant DSTVController
  DSTVController->>App: envelope
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
| 500 | 500 | BE-ERR-DSTV-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-DSTV-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-DSTV-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-DigitalSubscription/TZTigoSuperAppDigitalSubscription/Controllers/DSTVController.cs › DSTVController.CustomerDetailenc` @ `fd31aa1`
- Decrypted DTO `CustomerDetailRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
