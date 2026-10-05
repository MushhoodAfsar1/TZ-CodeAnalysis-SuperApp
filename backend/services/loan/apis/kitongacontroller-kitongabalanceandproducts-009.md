---
kb_section: backend
type: api-contract
ids: [BE-API-LOAN-009]
service: LOAN
repo: TZ-Tigo-SuperApp-Loan
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 759a471
updated: 2026-10-05
confidence: confirmed
---

# BE-API-LOAN-009 KitongaController.KitongaBalanceAndProducts
**Service:** BE-SVC-LOAN · **Handler:** `TZ-Tigo-SuperApp-Loan/TZTigoSuperAppLoan/Controllers/KitongaController.cs › KitongaController.KitongaBalanceAndProducts` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Kitonga/KitongaBalanceAndProducts
  internal_path: /api/Kitonga/KitongaBalanceAndProducts
  dispatch_field: null
  dispatch_value: null
  controller_action: KitongaController.KitongaBalanceAndProducts
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Kitonga/KitongaBalanceAndProducts`
- **Auth / filters:** SessionValidationFilter (X-User-Session), EncryptionProviderFilter<KitongaLoanRequestDto>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `KitongaLoanRequestDto`

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
| `sessionId` | `string` | N | — | shape only | sessionId |
| `requestId` | `string` | N | — | shape only | requestId |
| `channelId` | `string` | N | — | shape only | channelId |
| `countryCode` | `string` | N | — | shape only | countryCode |
| `languageId` | `string` | N | — | shape only | languageId |
| `msisdn` | `string` | N | — | shape only | msisdn |
| `accountId` | `string` | N | — | shape only | accountId |
| `Pin` | `string` | N | — | shape only | Pin |
| `productCode` | `string` | N | — | shape only | productCode |
| `termDays` | `string` | N | — | shape only | termDays |
| `PaymentMethod` | `string?` | N | — | shape only | PaymentMethod |
| `loanId` | `string?` | N | — | shape only | loanId |
| `amount` | `float` | N | — | shape only | amount |

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
  "sessionId": "<string>",
  "requestId": "<string>",
  "channelId": "<string>",
  "countryCode": "<string>",
  "languageId": "<string>",
  "msisdn": "255XXXXXXXXX",
  "accountId": "<string>",
  "Pin": "<encrypted-pin>",
  "productCode": "<string>",
  "termDays": "<string>",
  "PaymentMethod": "<string>",
  "loanId": "<string>",
  "amount": "<amount>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt `payload` with AES when config `is_encrypted`/`isEncrypted` is true; else JSON-deserialize | Filter stores raw string; later cast may fail → 500 | — | `TZ-Tigo-SuperApp-Loan/TZTigoSuperAppLoan/Controllers/KitongaController.cs › KitongaController.KitongaBalanceAndProducts` |
| 2 | Validate `X-User-Session` JWT (`TokenKey`) then Redis/DB token | HTTP 410 envelope | BE-BR-LOAN-001 | `TZ-Tigo-SuperApp-Loan › SessionValidationFilter` |
| 3 | `creditScoreResponse.success == true \|\| CustomerLoanProductsResponse.success == true \|\| QueryOutstandingLoanResponse.success == true` | branch / error envelope | — | `TZ-Tigo-SuperApp-Loan/TZTigoSuperAppLoan/Controllers/KitongaController.cs › KitongaController.KitongaBalanceAndProducts` |
| 4 | `isSuccess` | branch / error envelope | — | `TZ-Tigo-SuperApp-Loan/TZTigoSuperAppLoan/Controllers/KitongaController.cs › KitongaController.KitongaBalanceAndProducts` |
| 5 | `loanResponse?.body?.products is not null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Loan/TZTigoSuperAppLoan/Controllers/KitongaController.cs › KitongaController.KitongaBalanceAndProducts` |
| 6 | `string.Equals(loan?.loanRepaymentServices, installmentService, StringComparison.OrdinalIgnoreCase` | branch / error envelope | — | `TZ-Tigo-SuperApp-Loan/TZTigoSuperAppLoan/Controllers/KitongaController.cs › KitongaController.KitongaBalanceAndProducts` |
| 7 | `response?.header?.code == "LoanEngine-05-0000-S" \|\| response?.header?.code == "LoanEngine-1001-162-V"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Loan/TZTigoSuperAppLoan/Controllers/KitongaController.cs › KitongaController.KitongaBalanceAndProducts` |

## Internal call chain
1. Client POST `/api/Kitonga/KitongaBalanceAndProducts` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `KitongaLoanRequestDto` on `HttpContext.Items['modeldata']`.
3. SessionValidationFilter validates `X-User-Session`.
4. `KitongaController.KitongaBalanceAndProducts` runs (`TZ-Tigo-SuperApp-Loan/TZTigoSuperAppLoan/Controllers/KitongaController.cs`).
5. Calls `Utilities.GenerateReference`.
6. Calls `_kitongaLoanRepository.GetCreditScore`.
7. Calls `_kitongaLoanRepository.GetCustomerLoanProducts`.
8. Calls `_kitongaLoanRepository.QueryOutstandingLoan`.
9. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  participant EncFilter
  App->>EncFilter: POST payload envelope
  EncFilter->>EncFilter: AES decrypt payload
  EncFilter->>KitongaController: Items['modeldata']
  participant KitongaController
  KitongaController->>Utilities: GenerateReference()
  KitongaController->>_kitongaLoanRepository: GetCreditScore()
  KitongaController->>_kitongaLoanRepository: GetCustomerLoanProducts()
  KitongaController->>_kitongaLoanRepository: QueryOutstandingLoan()
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
- `TZ-Tigo-SuperApp-Loan/TZTigoSuperAppLoan/Controllers/KitongaController.cs › KitongaController.KitongaBalanceAndProducts` @ `759a471`
- Decrypted DTO `KitongaLoanRequestDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
