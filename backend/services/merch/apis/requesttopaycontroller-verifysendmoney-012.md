---
kb_section: backend
type: api-contract
ids: [BE-API-MERCH-012]
service: MERCH
repo: TZ-Tigo-SuperApp-Merchant
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 2367767
updated: 2026-10-05
confidence: confirmed
---

# BE-API-MERCH-012 RequestToPayController.VerifySendMoney
**Service:** BE-SVC-MERCH · **Handler:** `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs › RequestToPayController.VerifySendMoney` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/RequestToPay/VerifySendMoney
  internal_path: /api/RequestToPay/VerifySendMoney
  dispatch_field: null
  dispatch_value: null
  controller_action: RequestToPayController.VerifySendMoney
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/RequestToPay/VerifySendMoney`
- **Auth / filters:** SessionValidationFilter (X-User-Session), EncryptionProviderFilter<VerifySendMoneyRequest>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `VerifySendMoneyRequest`

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
| `sendMoney` | `List<SendMoney>` | Y | legs | foreach | R2P verify |
| `sendMoney[].referenceID` | `string?` | Y for R2P | load RequestToPay | repository | R2P id |
| `sendMoney[].sourceMSISDN` / `targetMSISDN` / `amount` / `shortCode` / `inclCOFee` | string/bool | Y | TANQR map | repository | MMP fee |

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
  "pushId": "<push-token>",
  "deviceType": "<string>",
  "sendMoney": []
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt + session | 500 / 410 | BE-BR-MERCH-001 | `RequestToPayController.VerifySendMoney` |
| 2 | If referenceID set, load R2P; null → Invalid Reference; APPROVED/FAILED/expired → 400 | 400 | — | `RequestToPayService.VerifySendMoney` |
| 3 | Stamp Tanzania:ConsumerID; TANQR via GetShortcodeAsync | 400 alias | — | same |
| 4 | SOAP CalculateFee **only** `VerifySendMoneyTigoToTigoURL` (no Other rail); ResultCode 0 attaches ExpiryTime/Description | fail | — | same |

## Internal call chain
1. Client POST `/api/RequestToPay/VerifySendMoney` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `VerifySendMoneyRequest` on `HttpContext.Items['modeldata']`.
3. SessionValidationFilter validates `X-User-Session`.
4. `RequestToPayController.VerifySendMoney` runs (`TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs`).
5. Calls `_requestToPayService.VerifySendMoney`.
6. Calls `_apiResponseHandler.ResponseObject`.
7. Calls `_apiResponseHandler.CreateResponse`.
8. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  participant EncFilter
  App->>EncFilter: POST payload envelope
  EncFilter->>EncFilter: AES decrypt payload
  EncFilter->>RequestToPayController: Items['modeldata']
  participant RequestToPayController
  RequestToPayController->>_requestToPayService: VerifySendMoney()
  RequestToPayController->>_apiResponseHandler: ResponseObject()
  RequestToPayController->>_apiResponseHandler: CreateResponse()
  RequestToPayController->>_logger: LogError()
```

## Downstream
| Order | Target | Sync/Async | Condition | Sent / used fields |
|---|---|---|---|---|
| 1 | SOAP CalculateFee `VerifySendMoneyTigoToTigoURL` | Sync | always (Tigo-only) | sendMoney[] + Tanzania:ConsumerID |
| 2 | EF RequestToPay | R | referenceID set | status/expiry |

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
- `Tanzania:ConsumerID`, `TANQR`, `VerifySendMoneyTigoToTigoURL`

## Evidence
- `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/RequestToPayController.cs › RequestToPayController.VerifySendMoney` @ `2367767`
- Decrypted DTO `VerifySendMoneyRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
