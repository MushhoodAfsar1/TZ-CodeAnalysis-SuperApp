---
kb_section: backend
type: api-contract
ids: [BE-API-SEND-009]
service: SEND
repo: TZ-Tigo-SuperApp-SendMoney
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 599771b
updated: 2026-10-05
confidence: confirmed
---

# BE-API-SEND-009 ATMCashoutController.ATMCashoutGenerateOtp
**Service:** BE-SVC-SEND · **Handler:** `TZ-Tigo-SuperApp-SendMoney/TZTigoSuperAppSendMoney/Controllers/ATMCashoutController.cs › ATMCashoutController.ATMCashoutGenerateOtp` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/ATMCashout/ATMCashoutGenerateOtp
  internal_path: /api/ATMCashout/ATMCashoutGenerateOtp
  dispatch_field: null
  dispatch_value: null
  controller_action: ATMCashoutController.ATMCashoutGenerateOtp
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/ATMCashout/ATMCashoutGenerateOtp`
- **Auth / filters:** SessionValidationFilter (X-User-Session), EncryptionProviderFilter<ATMCashoutGenerateOtpRequest>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `ATMCashoutGenerateOtpRequest`

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
| `AtmId` | `string?` | N | — | shape only | AtmId |
| `CustomerMSISDN` | `string?` | N | — | shape only | CustomerMSISDN |
| `Amount` | `string?` | N | — | shape only | Amount |
| `PIN` | `string?` | N | — | shape only | PIN |

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
  "AtmId": "<string>",
  "CustomerMSISDN": "255XXXXXXXXX",
  "Amount": "<amount>",
  "PIN": "<encrypted-pin>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt | 500 | — | `ATMCashOutController.ATMCashOutGenerateOTP` |
| 2 | ATM token (same as bank list) | 400 Invalid token | — | `ATMCashoutService.GenerateOTP` |
| 3 | Insert `ATMTransactions` (sappRefId) | — | — | same |
| 4 | POST `ATMCashout:CashoutGenerateOtp` (AtmId, CustomerMSISDN, Amount, PIN) | update row; fail envelope | — | same |
| 5 | HTTP OK + `ResponseStatus` | fail | — | same |

## Internal call chain
1. Client POST `/api/ATMCashout/ATMCashoutGenerateOtp` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `ATMCashoutGenerateOtpRequest` on `HttpContext.Items['modeldata']`.
3. SessionValidationFilter validates `X-User-Session`.
4. `ATMCashoutController.ATMCashoutGenerateOtp` runs (`TZ-Tigo-SuperApp-SendMoney/TZTigoSuperAppSendMoney/Controllers/ATMCashoutController.cs`).
5. Calls `_cashoutService.GenerateOTP`.
6. Calls `_apiResponseHandler.CreateResponse`.
7. Calls `_apiResponseHandler.CreateResponse`.
8. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  participant EncFilter
  App->>EncFilter: POST payload envelope
  EncFilter->>EncFilter: AES decrypt payload
  EncFilter->>ATMCashoutController: Items['modeldata']
  participant ATMCashoutController
  ATMCashoutController->>_cashoutService: GenerateOTP()
  ATMCashoutController->>_apiResponseHandler: CreateResponse()
  ATMCashoutController->>_logger: LogError()
```

## Downstream
| Order | Target | Sync/Async | Condition | Sent / used fields |
|---|---|---|---|---|
| 1 | HTTP token `ATMCashout:GetToken` | Sync | cache miss | grant keys |
| 2 | HTTP `ATMCashout:CashoutGenerateOtp` | Sync | token ok | AtmId, MSISDN, Amount, PIN |
| 3 | EF `ATMTransactions` | Sync | always | insert+update |

## Data touched
| Entity / table / SP | R/W | Notes |
|---|---|---|
| `ATMTransactions` | W | sappRefId + partner response |

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
- `ATMCashout:GetToken`, `Grant_Type`, `Username`, `Password`, `ATMCashout:CashoutGenerateOtp`

## Evidence
- `TZ-Tigo-SuperApp-SendMoney/TZTigoSuperAppSendMoney/Controllers/ATMCashoutController.cs › ATMCashoutController.ATMCashoutGenerateOtp` @ `599771b`
- Decrypted DTO `ATMCashoutGenerateOtpRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
