---
kb_section: backend
type: api-contract
ids: [BE-API-LOAN-020]
service: LOAN
repo: TZ-Tigo-SuperApp-Loan
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 759a471
updated: 2026-10-05
confidence: confirmed
---

# BE-API-LOAN-020 KitongaController.enc
**Service:** BE-SVC-LOAN · **Handler:** `TZ-Tigo-SuperApp-Loan/TZTigoSuperAppLoan/Controllers/KitongaController.cs › KitongaController.enc` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Kitonga/enc
  internal_path: /api/Kitonga/enc
  dispatch_field: null
  dispatch_value: null
  controller_action: KitongaController.enc
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Kitonga/enc`
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
| `productCode` | `string?` | N | — | shape only | productCode |
| `loanAmount` | `string?` | N | — | shape only | loanAmount |
| `dueDate` | `string?` | N | — | shape only | dueDate |
| `installmentOptions` | `List<installmentOptions>` | N | — | shape only | installmentOptions |

Headers / route / query params: none parsed beyond action signature `[('mod', 'LoanInstallmentRequest')]`

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
  "productCode": "<string>",
  "loanAmount": "<amount>",
  "dueDate": "<string>",
  "installmentOptions": []
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | No explicit guard parsed in action body | — | — | static parse |

## Internal call chain
1. Client POST `/api/Kitonga/enc`.
2. `KitongaController.enc` runs (`TZ-Tigo-SuperApp-Loan/TZTigoSuperAppLoan/Controllers/KitongaController.cs`).
3. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>KitongaController: POST /api/Kitonga/enc
  participant KitongaController
  KitongaController->>App: envelope
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
| 500 | 500 | BE-ERR-LOAN-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-LOAN-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-LOAN-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-Loan/TZTigoSuperAppLoan/Controllers/KitongaController.cs › KitongaController.enc` @ `759a471`
- Decrypted DTO `LoanInstallmentRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
