---
kb_section: backend
type: api-contract
ids: [BE-API-SELFC-027]
service: SELFC
repo: TZ-Tigo-SuperApp-SelfCare
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: a0aeca8
updated: 2026-10-05
confidence: confirmed
---

# BE-API-SELFC-027 SelfCareController.mMyNumberOTP
**Service:** BE-SVC-SELFC · **Handler:** `TZ-Tigo-SuperApp-SelfCare/TZTigoSuperAppSelfcare/Controllers/SelfCareController.cs › SelfCareController.mMyNumberOTP` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/SelfCare/MyNumberOtp
  internal_path: /api/SelfCare/MyNumberOtp
  dispatch_field: null
  dispatch_value: null
  controller_action: SelfCareController.mMyNumberOTP
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/SelfCare/MyNumberOtp`
- **Auth / filters:** SessionValidationFilter (X-User-Session), EncryptionProviderFilter<SendMyNumberOTPRequest>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `SendMyNumberOTPRequest`

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
| `geoCode` | `string?` | N | — | shape only | geoCode |
| `deviceType` | `string?` | N | — | shape only | deviceType |
| `userCaseName` | `string?` | N | — | shape only | userCaseName |
| `accessToken` | `string?` | N | — | shape only | accessToken |
| `pushId` | `string?` | N | — | shape only | pushId |

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
  "geoCode": "<string>",
  "deviceType": "<string>",
  "userCaseName": "<string>",
  "accessToken": "<jwt>",
  "pushId": "<push-token>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt `payload` with AES when config `is_encrypted`/`isEncrypted` is true; else JSON-deserialize | Filter stores raw string; later cast may fail → 500 | — | `TZ-Tigo-SuperApp-SelfCare/TZTigoSuperAppSelfcare/Controllers/SelfCareController.cs › SelfCareController.mMyNumberOTP` |
| 2 | Validate `X-User-Session` JWT (`TokenKey`) then Redis/DB token | HTTP 410 envelope | BE-BR-SELFC-001 | `TZ-Tigo-SuperApp-SelfCare › SessionValidationFilter` |
| 3 | `request.msisdn != request.linkmsisdn` | branch / error envelope | — | `TZ-Tigo-SuperApp-SelfCare/TZTigoSuperAppSelfcare/Controllers/SelfCareController.cs › SelfCareController.mMyNumberOTP` |
| 4 | `!numberExists` | branch / error envelope | — | `TZ-Tigo-SuperApp-SelfCare/TZTigoSuperAppSelfcare/Controllers/SelfCareController.cs › SelfCareController.mMyNumberOTP` |
| 5 | `isAgent` | branch / error envelope | — | `TZ-Tigo-SuperApp-SelfCare/TZTigoSuperAppSelfcare/Controllers/SelfCareController.cs › SelfCareController.mMyNumberOTP` |
| 6 | `!string.IsNullOrEmpty(responseCode` | branch / error envelope | — | `TZ-Tigo-SuperApp-SelfCare/TZTigoSuperAppSelfcare/Controllers/SelfCareController.cs › SelfCareController.mMyNumberOTP` |
| 7 | `_configuration.GetValue<string>("EnableLog:Error"` | branch / error envelope | — | `TZ-Tigo-SuperApp-SelfCare/TZTigoSuperAppSelfcare/Controllers/SelfCareController.cs › SelfCareController.mMyNumberOTP` |
| 8 | `param is string` | branch / error envelope | — | `TZ-Tigo-SuperApp-SelfCare/TZTigoSuperAppSelfcare/Controllers/SelfCareController.cs › SelfCareController.mMyNumberOTP` |

## Internal call chain
1. Client POST `/api/SelfCare/MyNumberOtp` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `SendMyNumberOTPRequest` on `HttpContext.Items['modeldata']`.
3. SessionValidationFilter validates `X-User-Session`.
4. `SelfCareController.mMyNumberOTP` runs (`TZ-Tigo-SuperApp-SelfCare/TZTigoSuperAppSelfcare/Controllers/SelfCareController.cs`).
5. Calls `_selfCareService.mMyNumberOTP`.
6. Calls `_responseHandler.CreateResponse`.
7. Calls `_responseHandler.CreateResponse`.
8. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  participant EncFilter
  App->>EncFilter: POST payload envelope
  EncFilter->>EncFilter: AES decrypt payload
  EncFilter->>SelfCareController: Items['modeldata']
  participant SelfCareController
  SelfCareController->>_selfCareService: mMyNumberOTP()
  SelfCareController->>_responseHandler: CreateResponse()
  SelfCareController->>_logger: LogError()
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
| 500 | 500 | BE-ERR-SELFC-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-SELFC-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-SELFC-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-SelfCare/TZTigoSuperAppSelfcare/Controllers/SelfCareController.cs › SelfCareController.mMyNumberOTP` @ `a0aeca8`
- Decrypted DTO `SendMyNumberOTPRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
