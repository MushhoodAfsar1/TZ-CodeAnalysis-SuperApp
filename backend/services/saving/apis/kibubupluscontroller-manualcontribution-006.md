---
kb_section: backend
type: api-contract
ids: [BE-API-SAVING-006]
service: SAVING
repo: TZ-Tigo-SuperApp-Saving
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 2ca8791
updated: 2026-10-05
confidence: confirmed
---

# BE-API-SAVING-006 KibubuPlusController.ManualContribution
**Service:** BE-SVC-SAVING · **Handler:** `TZ-Tigo-SuperApp-Saving/TZTigoSuperAppSaving/Controllers/KibubuPlusController.cs › KibubuPlusController.ManualContribution` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/KibubuPlus/ManualContribution
  internal_path: /api/KibubuPlus/ManualContribution
  dispatch_field: null
  dispatch_value: null
  controller_action: KibubuPlusController.ManualContribution
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/KibubuPlus/ManualContribution`
- **Auth / filters:** SessionValidationFilter (X-User-Session), EncryptionProviderFilter<ManualContributionRequest>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `ManualContributionRequest`

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `requestingOrganisationTransactionReference` | `string?` | N | — | shape only | requestingOrganisationTransactionReference |
| `requestId` | `string?` | N | — | shape only | requestId |
| `channel` | `string?` | N | — | shape only | channel |
| `ipInfo` | `string?` | N | — | shape only | ipInfo |
| `appVersion` | `string?` | N | — | shape only | appVersion |
| `languageCode` | `string?` | N | — | shape only | languageCode |
| `pushId` | `string?` | N | — | shape only | pushId |
| `deviceType` | `string?` | N | — | shape only | deviceType |
| `deviceId` | `string?` | N | — | shape only | deviceId |
| `deviceMaker` | `string?` | N | — | shape only | deviceMaker |
| `oS` | `string?` | N | — | shape only | oS |
| `geoCode` | `string?` | N | — | shape only | geoCode |
| `userCaseName` | `string?` | N | — | shape only | userCaseName |
| `accessToken` | `string?` | N | — | shape only | accessToken |
| `msisdn` | `string` | Y | — | [Required] | msisdn |
| `planId` | `string` | Y | — | [Required] | planId |
| `pin` | `string` | Y | — | [Required] | pin |
| `amount` | `string` | Y | — | [Required] | amount |

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
  "pushId": "<push-token>",
  "deviceType": "<string>",
  "deviceId": "<device-id>",
  "deviceMaker": "<string>",
  "oS": "<string>",
  "geoCode": "<string>",
  "userCaseName": "<string>",
  "accessToken": "<jwt>",
  "msisdn": "255XXXXXXXXX",
  "planId": "<string>",
  "pin": "<encrypted-pin>",
  "amount": "<amount>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt + session | 500 / 410 | BE-BR-SAVING-001 | `KibubuPlusController.ManualContribution` |
| 2 | Nested header/body HTTP; success `LoanEngine-1001-204-S` | fail | — | `KibubuPlusRepository.ManualContribution` |

## Internal call chain
1. Client POST `/api/KibubuPlus/ManualContribution` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `ManualContributionRequest` on `HttpContext.Items['modeldata']`.
3. SessionValidationFilter validates `X-User-Session`.
4. `KibubuPlusController.ManualContribution` runs (`TZ-Tigo-SuperApp-Saving/TZTigoSuperAppSaving/Controllers/KibubuPlusController.cs`).
5. Calls `Utilities.ValidateRequest`.
6. Calls `_repository.ManualContribution`.
7. Calls `_apiResponseHandler.CreateResponse`.
8. Calls `_apiResponseHandler.CreateResponse`.
9. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  participant EncFilter
  App->>EncFilter: POST payload envelope
  EncFilter->>EncFilter: AES decrypt payload
  EncFilter->>KibubuPlusController: Items['modeldata']
  participant KibubuPlusController
  KibubuPlusController->>Utilities: ValidateRequest()
  KibubuPlusController->>_repository: ManualContribution()
  KibubuPlusController->>_apiResponseHandler: CreateResponse()
  KibubuPlusController->>_logger: LogError()
```

## Downstream
| Order | Target | Sync/Async | Condition | Sent / used fields |
|---|---|---|---|---|
| 1 | HTTP `KibubuPlus:ManualContributionUrl` | Sync | always | msisdn, pin, amount / plan fields |

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
| 500 | 500 | BE-ERR-SAVING-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-SAVING-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-SAVING-001` (when session filter present).

## Config keys
- `KibubuPlus:ManualContributionUrl`, `KibubuPlus:BasicToken`, `TokenKey`

## Evidence
- `TZ-Tigo-SuperApp-Saving/TZTigoSuperAppSaving/Controllers/KibubuPlusController.cs › KibubuPlusController.ManualContribution` @ `2ca8791`
- Decrypted DTO `ManualContributionRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
