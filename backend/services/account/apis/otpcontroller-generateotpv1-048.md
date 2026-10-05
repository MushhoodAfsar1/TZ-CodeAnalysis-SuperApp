---
kb_section: backend
type: api-contract
ids: [BE-API-ACCOUNT-048]
service: ACCOUNT
repo: TZ-Tigo-SuperApp-Account
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 5c549d6
updated: 2026-10-05
confidence: confirmed
---

# BE-API-ACCOUNT-048 OtpController.GenerateOtpV1
**Service:** BE-SVC-ACCOUNT · **Handler:** `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/OtpController.cs › OtpController.GenerateOtpV1` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Otp/GenerateOtpV1
  internal_path: /api/Otp/GenerateOtpV1
  dispatch_field: null
  dispatch_value: null
  controller_action: OtpController.GenerateOtpV1
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Otp/GenerateOtpV1`
- **Auth / filters:** EncryptionProviderFilter<GenerateOtpRequest>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `GenerateOtpRequest`

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
| `deviceType` | `string?` | N | — | shape only | deviceType |
| `oS` | `string?` | N | — | shape only | oS |
| `pushId` | `string?` | N | — | shape only | pushId |
| `geoCode` | `string?` | N | — | shape only | geoCode |
| `latitude` | `string?` | N | — | shape only | latitude |
| `longitude` | `string?` | N | — | shape only | longitude |
| `useCaseName` | `string?` | N | — | shape only | useCaseName |
| `accessToken` | `string?` | N | — | shape only | accessToken |
| `msisdn` | `string?` | N | — | shape only | msisdn |

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
  "deviceType": "<string>",
  "oS": "<string>",
  "pushId": "<push-token>",
  "geoCode": "<string>",
  "latitude": "<lat>",
  "longitude": "<lng>",
  "useCaseName": "<string>",
  "accessToken": "<jwt>",
  "msisdn": "255XXXXXXXXX"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt | 500 | — | `OtpController.GenerateOtpV1` |
| 2 | Profile; device-limit; V1 temp-block / resend UM-Lo-10/11 | blocked | BE-BR-ACCOUNT-OTP | `OtpService.GenerateOtpV1` |
| 3 | SMS success UM-Lo-08 | fail | — | same |

## Internal call chain
1. Client POST `/api/Otp/GenerateOtpV1` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `GenerateOtpRequest` on `HttpContext.Items['modeldata']`.
3. `OtpController.GenerateOtpV1` runs (`TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/OtpController.cs`).
4. Calls `_otpService.GenerateOtpV1`.
5. Calls `_responseHandler.CreateResponse`.
6. Calls `this.StatusCode`.
7. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  participant EncFilter
  App->>EncFilter: POST payload envelope
  EncFilter->>EncFilter: AES decrypt payload
  EncFilter->>OtpController: Items['modeldata']
  participant OtpController
  OtpController->>_otpService: GenerateOtpV1()
  OtpController->>_responseHandler: CreateResponse()
  OtpController->>_logger: LogError()
```

## Downstream
| Order | Target | Sync/Async | Condition | Sent / used fields |
|---|---|---|---|---|
| 1 | SMS `SendSMS` + optional `SendEMail` | Sync | always | msisdn |

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
| 500 | 500 | BE-ERR-ACCOUNT-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-ACCOUNT-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-ACCOUNT-001` (when session filter present).

## Config keys
- same keys as GenerateOtp plus `InvalidOtpLimit` / `TempBlockOtpTimeLimit` appconfig

## Evidence
- `TZ-Tigo-SuperApp-Account/TZTigoSuperAppAccount/Controllers/OtpController.cs › OtpController.GenerateOtpV1` @ `5c549d6`
- Decrypted DTO `GenerateOtpRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
