---
kb_section: backend
type: api-contract
ids: [BE-API-WALLET-001]
service: WALLET
repo: TZ-Tigo-SuperApp-Wallet
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 27737b1
updated: 2026-10-05
confidence: confirmed
---

# BE-API-WALLET-001 CashOutController.CashOutFee
**Service:** BE-SVC-WALLET · **Handler:** `TZ-Tigo-SuperApp-Wallet/TZTigoSuperAppWallet/Controllers/CashOutController.cs › CashOutController.CashOutFee` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/CashOut/cashOutFee
  internal_path: /api/CashOut/cashOutFee
  dispatch_field: null
  dispatch_value: null
  controller_action: CashOutController.CashOutFee
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/CashOut/cashOutFee`
- **Auth / filters:** SessionValidationFilter (X-User-Session), EncryptionProviderFilter<CashOutFeeRequestDto>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `CashOutFeeRequestDto`

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `requestingOrganisationTransactionReference` | `string?` | N | — | shape only | requestingOrganisationTransactionReference |
| `requestID` | `string?` | N | — | shape only | requestID |
| `iPInfo` | `string?` | N | — | shape only | iPInfo |
| `geoCode` | `string?` | N | — | shape only | geoCode |
| `useCaseName` | `string?` | N | — | shape only | useCaseName |
| `channel` | `string?` | N | — | shape only | channel |
| `pushId` | `string?` | N | — | shape only | pushId |
| `deviceType` | `string?` | N | — | shape only | deviceType |
| `appVersion` | `string?` | N | — | shape only | appVersion |
| `languageCode` | `string?` | N | — | shape only | languageCode |
| `deviceId` | `string?` | N | — | shape only | deviceId |
| `deviceMaker` | `string?` | N | — | shape only | deviceMaker |
| `oS` | `string?` | N | — | shape only | oS |
| `accesstoken` | `string?` | N | — | shape only | accesstoken |
| `consumerID` | `string` | N | — | shape only | consumerID |
| `country` | `string` | N | — | shape only | country |
| `correlationID` | `string` | N | — | shape only | correlationID |
| `msisdn` | `string` | N | — | shape only | msisdn |
| `creditParty` | object `{ key, value }` | N | nested (not array, not string) | SOAP uses `creditParty.value` as agent/target id | cash-out destination |
| `creditParty.key` | `string?` | N | — | shape | party key |
| `creditParty.value` | `string?` | Y (for SOAP) | — | `CashOutService.CashOutFee` | agent / credit party id |
| `amount` | `string` | N | — | shape only | amount |
| `transactionType` | `string` | N | — | shape only | transactionType |
| `shortCode` | `string` | N | — | shape only | shortCode |

Headers / route / query params: none parsed beyond action signature `[('msg', 'RequestModel')]`

Sample (synthetic):
```json
{"payload": "<ciphertext-or-json>"}
# decrypted payload:
{
  "requestingOrganisationTransactionReference": "<string>",
  "requestID": "<string>",
  "iPInfo": "<encrypted-pin>",
  "geoCode": "<string>",
  "useCaseName": "<string>",
  "channel": "<string>",
  "pushId": "<push-token>",
  "deviceType": "<string>",
  "appVersion": "<string>",
  "languageCode": "<string>",
  "deviceId": "<device-id>",
  "deviceMaker": "<string>",
  "oS": "<string>",
  "accesstoken": "<jwt>",
  "consumerID": "<string>",
  "country": "<string>",
  "correlationID": "<string>",
  "msisdn": "255XXXXXXXXX",
  "creditParty": { "key": "<key>", "value": "<agent-id>" },
  "amount": "<amount>",
  "transactionType": "<string>",
  "shortCode": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt `payload` when `isEncrypted` else JSON | filter/cast fail → 500 | — | `TZ-Tigo-SuperApp-Wallet/TZTigoSuperAppWallet/Controllers/CashOutController.cs › CashOutController.CashOutFee` |
| 2 | `X-User-Session` JWT (`TokenKey`) + Redis/DB | HTTP 410 | BE-BR-WALLET-001 | `TZ-Tigo-SuperApp-Wallet › SessionValidationFilter` |
| 3 | SOAP CalculateFee POST (`CashOutFee`); PIN in SOAP is hard-coded `"0000"` | HTTP/SOAP error | BE-BR-WALLET-002 | `TZ-Tigo-SuperApp-Wallet/TZTigoSuperAppWallet/Services/CashOutService.cs › CashOutService.CashOutFee` |
| 4 | Success iff `response.code.ToLower() == "calculatefee-3031-0000-s"` | fail envelope with SOAP status/code/description | BE-BR-WALLET-002 | same |
| 5 | Unhandled | HTTP 500 | BE-ERR-WALLET-001 | controller catch |

## Internal call chain
1. Client POST `/api/CashOut/cashOutFee` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `CashOutFeeRequestDto` on `HttpContext.Items['modeldata']`.
3. SessionValidationFilter validates `X-User-Session`.
4. `CashOutController.CashOutFee` runs (`TZ-Tigo-SuperApp-Wallet/TZTigoSuperAppWallet/Controllers/CashOutController.cs`).
5. Calls `_cashoutservice.CashOutFee`.
6. Calls `code.ToLower`.
7. Calls `_responseHandler.CreateResponse`.
8. Calls `_responseHandler.CreateResponse`.
9. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  participant EncFilter
  App->>EncFilter: POST payload envelope
  EncFilter->>EncFilter: AES decrypt payload
  EncFilter->>CashOutController: Items['modeldata']
  participant CashOutController
  CashOutController->>_cashoutservice: CashOutFee()
  CashOutController->>code: ToLower()
  CashOutController->>_responseHandler: CreateResponse()
```

## Downstream
| Order | Target (BE-API / BE-INT / BE-EVT) | Sync/Async | Condition | Sent / used fields |
|---|---|---|---|---|
| 1 | MMP SOAP CalculateFee via config key `CashOutFee` | Sync | always | msisdn, amount, `creditParty.value`, shortCode, consumerID; auth keys `Tanzania:Username`, `Tanzania:Password`, `Tanzania:ConsumerID` |
| 2 | BE-API-CONFIG ResponseCodeApp | Sync | after handler | responseCode, language, channel |

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
| 500 | 500 | BE-ERR-WALLET-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-WALLET-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-WALLET-001` (when session filter present).

## Config keys
- `isEncrypted`, `TokenKey`, `responseChanel`, `serviceName`
- SOAP URL key `CashOutFee`; `Tanzania:Username`, `Tanzania:Password`, `Tanzania:ConsumerID`

## Evidence
- `TZ-Tigo-SuperApp-Wallet/TZTigoSuperAppWallet/Controllers/CashOutController.cs › CashOutController.CashOutFee` @ `27737b1`
- Decrypted DTO `CashOutFeeRequestDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
