---
kb_section: backend
type: api-contract
ids: [BE-API-LOAN-003]
service: LOAN
repo: TZ-Tigo-SuperApp-Loan
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 759a471
updated: 2026-10-05
confidence: confirmed
---

# BE-API-LOAN-003 LoanManagementController.UnsubscribeLoan
**Service:** BE-SVC-LOAN · **Handler:** `TZ-Tigo-SuperApp-Loan/TZTigoSuperAppLoan/Controllers/LoanManagementController.cs › LoanManagementController.UnsubscribeLoan` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/LoanManagement/UnsubscribeLoan
  internal_path: /api/LoanManagement/UnsubscribeLoan
  dispatch_field: null
  dispatch_value: null
  controller_action: LoanManagementController.UnsubscribeLoan
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/LoanManagement/UnsubscribeLoan`
- **Auth / filters:** SessionValidationFilter (X-User-Session), EncryptionProviderFilter<UnsubscribeLoanRequest>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `UnsubscribeLoanRequest`

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
| `consumerID` | `string?` | N | — | shape only | consumerID |
| `referenceId` | `string?` | N | — | shape only | referenceId |
| `customerMsisdn` | `string?` | N | — | shape only | customerMsisdn |
| `pin` | `string?` | N | — | shape only | pin |
| `brandID` | `string?` | N | — | shape only | brandID |

Headers / route / query params: none parsed beyond action signature `[('msg', 'RequestModel')]`

Sample (synthetic):
```json
{"payload": "<ciphertext-or-json>"}
# decrypted payload:
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
  "consumerID": "<string>",
  "referenceId": "<string>",
  "customerMsisdn": "255XXXXXXXXX",
  "pin": "<encrypted-pin>",
  "brandID": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt + session | 500 / 410 | BE-BR-LOAN-001 | `LoanManagementController.UnsubscribeLoan` |
| 2 | SOAP MTPGOverDraftUnSubscribeReq; success responseCode==0 | fail envelope | — | `TZ-Tigo-SuperApp-Loan › LoanManagementRepository.UnsubscribeLoan` |

## Internal call chain
1. Client POST `/api/LoanManagement/UnsubscribeLoan` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `UnsubscribeLoanRequest` on `HttpContext.Items['modeldata']`.
3. SessionValidationFilter validates `X-User-Session`.
4. `LoanManagementController.UnsubscribeLoan` runs (`TZ-Tigo-SuperApp-Loan/TZTigoSuperAppLoan/Controllers/LoanManagementController.cs`).
5. Calls `_loanManagementRepository.UnsubscribeLoan`.
6. Calls `_apiResponseHandler.CreateResponse`.
7. Calls `_apiResponseHandler.CreateResponse`.
8. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  participant EncFilter
  App->>EncFilter: POST payload envelope
  EncFilter->>EncFilter: AES decrypt payload
  EncFilter->>LoanManagementController: Items['modeldata']
  participant LoanManagementController
  LoanManagementController->>_loanManagementRepository: UnsubscribeLoan()
  LoanManagementController->>_apiResponseHandler: CreateResponse()
  LoanManagementController->>_logger: LogError()
```

## Downstream
| Order | Target | Sync/Async | Condition | Sent / used fields |
|---|---|---|---|---|
| 1 | MMP XML overdraft | Sync | always | customerMsisdn, pin, brandID/amount |

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
- `Tanzania:UnsubscribeLoan`, `Tanzania:ConsumerID`, `TokenKey`

## Evidence
- `TZ-Tigo-SuperApp-Loan/TZTigoSuperAppLoan/Controllers/LoanManagementController.cs › LoanManagementController.UnsubscribeLoan` @ `759a471`
- Decrypted DTO `UnsubscribeLoanRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
