---
kb_section: backend
type: api-contract
ids: [BE-API-EXTPAY-003]
service: EXTPAY
repo: TZ-Tigo-SuperApp-ExternalPayment
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 51718e1
updated: 2026-10-05
confidence: confirmed
---

# BE-API-EXTPAY-003 ExternalPaymentController.GovernmentPaymentInquiry
**Service:** BE-SVC-EXTPAY · **Handler:** `TZ-Tigo-SuperApp-ExternalPayment/TZTigoSuperAppExternalPayment/Controllers/ExternalPaymentController.cs › ExternalPaymentController.GovernmentPaymentInquiry` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/ExternalPayment/GovernmentPaymentInquiry
  internal_path: /api/ExternalPayment/GovernmentPaymentInquiry
  dispatch_field: null
  dispatch_value: null
  controller_action: ExternalPaymentController.GovernmentPaymentInquiry
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/ExternalPayment/GovernmentPaymentInquiry`
- **Auth / filters:** SessionValidationFilter (X-User-Session), EncryptionProviderFilter<GovernmentPaymentInquiryRequest>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `GovernmentPaymentInquiryRequest`

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `requestingOrganisationTransactionReference` | `string?` | N | — | shape only | requestingOrganisationTransactionReference |
| `requestId` | `string?` | N | — | shape only | requestId |
| `channel` | `string?` | N | — | shape only | channel |
| `ipInfo` | `string?` | N | — | shape only | ipInfo |
| `appVersion` | `string?` | N | — | shape only | appVersion |
| `languageCode` | `string?` | N | — | shape only | languageCode |
| `deviceId` | `string?` | N | — | shape only | deviceId |
| `deviceType` | `string?` | N | — | shape only | deviceType |
| `pushId` | `string?` | N | — | shape only | pushId |
| `deviceMaker` | `string?` | N | — | shape only | deviceMaker |
| `oS` | `string?` | N | — | shape only | oS |
| `geoCode` | `string?` | N | — | shape only | geoCode |
| `userCaseName` | `string?` | N | — | shape only | userCaseName |
| `accessToken` | `string?` | N | — | shape only | accessToken |
| `PspCode` | `string?` | N | — | shape only | PspCode |
| `SysId` | `string?` | N | — | shape only | SysId |
| `ResultUrl` | `string?` | N | — | shape only | ResultUrl |
| `BillReqId` | `string?` | N | — | shape only | BillReqId |
| `AsseType` | `string` | N | — | shape only | AsseType |
| `AsseTypeValue` | `string` | N | — | shape only | AsseTypeValue |
| `SpCode` | `string?` | N | — | shape only | SpCode |
| `BillRsv1` | `string?` | N | — | shape only | BillRsv1 |
| `BillRsv2` | `string?` | N | — | shape only | BillRsv2 |
| `BillRsv3` | `string?` | N | — | shape only | BillRsv3 |
| `BillRsv4` | `string?` | N | — | shape only | BillRsv4 |
| `BillRsv5` | `string?` | N | — | shape only | BillRsv5 |

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
  "deviceType": "<string>",
  "pushId": "<push-token>",
  "deviceMaker": "<string>",
  "oS": "<string>",
  "geoCode": "<string>",
  "userCaseName": "<string>",
  "accessToken": "<jwt>",
  "PspCode": "<string>",
  "SysId": "<string>",
  "ResultUrl": "<string>",
  "BillReqId": "<string>",
  "AsseType": "<string>",
  "AsseTypeValue": "<string>",
  "SpCode": "<string>",
  "BillRsv1": "<string>",
  "BillRsv2": "<string>",
  "BillRsv3": "<string>",
  "BillRsv4": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt `payload` with AES when config `is_encrypted`/`isEncrypted` is true; else JSON-deserialize | Filter stores raw string; later cast may fail → 500 | — | `TZ-Tigo-SuperApp-ExternalPayment/TZTigoSuperAppExternalPayment/Controllers/ExternalPaymentController.cs › ExternalPaymentController.GovernmentPaymentInquiry` |
| 2 | Validate `X-User-Session` JWT (`TokenKey`) then Redis/DB token | HTTP 410 envelope | BE-BR-EXTPAY-001 | `TZ-Tigo-SuperApp-ExternalPayment › SessionValidationFilter` |
| 3 | `response.IsSuccessStatusCode == true` | branch / error envelope | — | `TZ-Tigo-SuperApp-ExternalPayment/TZTigoSuperAppExternalPayment/Controllers/ExternalPaymentController.cs › ExternalPaymentController.GovernmentPaymentInquiry` |
| 4 | `billStsCode.Count > 0 && billStsCode[0]?.InnerText == "7101"` | branch / error envelope | — | `TZ-Tigo-SuperApp-ExternalPayment/TZTigoSuperAppExternalPayment/Controllers/ExternalPaymentController.cs › ExternalPaymentController.GovernmentPaymentInquiry` |
| 5 | `_configuration.GetValue<string>("EnableLog:Error"` | branch / error envelope | — | `TZ-Tigo-SuperApp-ExternalPayment/TZTigoSuperAppExternalPayment/Controllers/ExternalPaymentController.cs › ExternalPaymentController.GovernmentPaymentInquiry` |
| 6 | `param is string` | branch / error envelope | — | `TZ-Tigo-SuperApp-ExternalPayment/TZTigoSuperAppExternalPayment/Controllers/ExternalPaymentController.cs › ExternalPaymentController.GovernmentPaymentInquiry` |

## Internal call chain
1. Client POST `/api/ExternalPayment/GovernmentPaymentInquiry` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `GovernmentPaymentInquiryRequest` on `HttpContext.Items['modeldata']`.
3. SessionValidationFilter validates `X-User-Session`.
4. `ExternalPaymentController.GovernmentPaymentInquiry` runs (`TZ-Tigo-SuperApp-ExternalPayment/TZTigoSuperAppExternalPayment/Controllers/ExternalPaymentController.cs`).
5. Calls `_submitPaymentRepository.GovernmentPaymentInquiry`.
6. Calls `_apiResponseHandler.CreateResponse`.
7. Calls `_apiResponseHandler.CreateResponse`.
8. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  participant EncFilter
  App->>EncFilter: POST payload envelope
  EncFilter->>EncFilter: AES decrypt payload
  EncFilter->>ExternalPaymentController: Items['modeldata']
  participant ExternalPaymentController
  ExternalPaymentController->>_submitPaymentRepository: GovernmentPaymentInquiry()
  ExternalPaymentController->>_apiResponseHandler: CreateResponse()
  ExternalPaymentController->>_logger: LogError()
```

## Downstream
| Order | Target (BE-API / BE-INT / BE-EVT) | Sync/Async | Condition | Sent / used fields |
|---|---|---|---|---|
| 1 | BE-API-CONFIG (ResponseCodeApp get-response-code-details) | Sync | after handler | responseCode, language, channel, optional service/method |

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
| 500 | 500 | BE-ERR-EXTPAY-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-EXTPAY-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-EXTPAY-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-ExternalPayment/TZTigoSuperAppExternalPayment/Controllers/ExternalPaymentController.cs › ExternalPaymentController.GovernmentPaymentInquiry` @ `51718e1`
- Decrypted DTO `GovernmentPaymentInquiryRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
