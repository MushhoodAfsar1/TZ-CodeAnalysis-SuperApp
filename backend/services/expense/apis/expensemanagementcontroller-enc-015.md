---
kb_section: backend
type: api-contract
ids: [BE-API-EXPENSE-015]
service: EXPENSE
repo: TZ-Tigo-SuperApp-Expense
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: e821ac9
updated: 2026-10-05
confidence: confirmed
---

# BE-API-EXPENSE-015 ExpenseManagementController.enc
**Service:** BE-SVC-EXPENSE · **Handler:** `TZ-Tigo-SuperApp-Expense/TZTigoSuperAppExpense/Controllers/ExpenseManagementController.cs › ExpenseManagementController.enc` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/ExpenseManagement/enc
  internal_path: /api/ExpenseManagement/enc
  dispatch_field: null
  dispatch_value: null
  controller_action: ExpenseManagementController.enc
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/ExpenseManagement/enc`
- **Auth / filters:** none on action (pipeline may still authorize)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `requestingOrganisationTransactionReference` | `string` | N | — | shape only | requestingOrganisationTransactionReference |
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
| `msisdn` | `string?` | N | — | shape only | msisdn |
| `pin` | `string?` | N | — | shape only | pin |
| `initiatorId` | `string?` | N | — | shape only | initiatorId |
| `requisitionId` | `string?` | N | — | shape only | requisitionId |
| `reason` | `string?` | N | — | shape only | reason |
| `paymentMode` | `string?` | N | — | shape only | paymentMode |
| `amountPaid` | `string?` | N | — | shape only | amountPaid |
| `amountSpent` | `string?` | N | — | shape only | amountSpent |
| `requestedMSISDN` | `string?` | N | — | shape only | requestedMSISDN |
| `iopType` | `string?` | N | — | shape only | iopType |
| `bankID` | `string?` | N | — | shape only | bankID |
| `accountNumber` | `string?` | N | — | shape only | accountNumber |
| `MFSTransactionID` | `string?` | N | — | shape only | MFSTransactionID |
| `file` | `string?` | N | — | shape only | file |

Headers / route / query params: none parsed beyond action signature `[('mod', 'CreateRetirementRequest')]`

Sample (synthetic):
```json
{
  "requestingOrganisationTransactionReference": "<string>",
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
  "msisdn": "255XXXXXXXXX",
  "pin": "<encrypted-pin>",
  "initiatorId": "<string>",
  "requisitionId": "<string>",
  "reason": "<string>",
  "paymentMode": "<string>",
  "amountPaid": "<amount>",
  "amountSpent": "<amount>",
  "requestedMSISDN": "255XXXXXXXXX",
  "iopType": "<string>",
  "bankID": "<string>",
  "accountNumber": "<account>",
  "MFSTransactionID": "<string>",
  "file": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | No explicit guard parsed in action body | — | — | static parse |

## Internal call chain
1. Client POST `/api/ExpenseManagement/enc`.
2. `ExpenseManagementController.enc` runs (`TZ-Tigo-SuperApp-Expense/TZTigoSuperAppExpense/Controllers/ExpenseManagementController.cs`).
3. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>ExpenseManagementController: POST /api/ExpenseManagement/enc
  participant ExpenseManagementController
  ExpenseManagementController->>App: envelope
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
| 500 | 500 | BE-ERR-EXPENSE-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-EXPENSE-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-EXPENSE-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-Expense/TZTigoSuperAppExpense/Controllers/ExpenseManagementController.cs › ExpenseManagementController.enc` @ `e821ac9`
- Decrypted DTO `CreateRetirementRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
