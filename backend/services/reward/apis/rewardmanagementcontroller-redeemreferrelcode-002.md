---
kb_section: backend
type: api-contract
ids: [BE-API-REWARD-002]
service: REWARD
repo: TZ-Tigo-SuperApp-RewardReferral
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: b47cb93
updated: 2026-10-05
confidence: confirmed
---

# BE-API-REWARD-002 RewardManagementController.RedeemReferrelCode
**Service:** BE-SVC-REWARD · **Handler:** `TZ-Tigo-SuperApp-RewardReferral/TZTigoSuperAppRewardReferral/Controllers/RewardManagementController.cs › RewardManagementController.RedeemReferrelCode` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/RewardManagement/RedeemReferrelCode
  internal_path: /api/RewardManagement/RedeemReferrelCode
  dispatch_field: null
  dispatch_value: null
  controller_action: RewardManagementController.RedeemReferrelCode
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/RewardManagement/RedeemReferrelCode`
- **Auth / filters:** SessionValidationFilter (X-User-Session), EncryptionProviderFilter<RedeemReferrelCodeRequest>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `RedeemReferrelCodeRequest`

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
| `msisdn` | `string?` | N | — | shape only | msisdn |
| `name` | `string?` | N | — | shape only | name |
| `refferelCode` | `string?` | N | — | shape only | refferelCode |
| `refferelLink` | `string?` | N | — | shape only | refferelLink |

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
  "msisdn": "255XXXXXXXXX",
  "name": "<string>",
  "refferelCode": "<string>",
  "refferelLink": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt `payload` with AES when config `is_encrypted`/`isEncrypted` is true; else JSON-deserialize | Filter stores raw string; later cast may fail → 500 | — | `TZ-Tigo-SuperApp-RewardReferral/TZTigoSuperAppRewardReferral/Controllers/RewardManagementController.cs › RewardManagementController.RedeemReferrelCode` |
| 2 | Validate `X-User-Session` JWT (`TokenKey`) then Redis/DB token | HTTP 410 envelope | BE-BR-REWARD-001 | `TZ-Tigo-SuperApp-RewardReferral › SessionValidationFilter` |
| 3 | `response.success == true` | branch / error envelope | — | `TZ-Tigo-SuperApp-RewardReferral/TZTigoSuperAppRewardReferral/Controllers/RewardManagementController.cs › RewardManagementController.RedeemReferrelCode` |
| 4 | `response.transactionStatus == "false" \|\| response.transactionStatus == "False"` | branch / error envelope | — | `TZ-Tigo-SuperApp-RewardReferral/TZTigoSuperAppRewardReferral/Controllers/RewardManagementController.cs › RewardManagementController.RedeemReferrelCode` |
| 5 | `_configuration.GetValue<string>("EnableLog:Information"` | branch / error envelope | — | `TZ-Tigo-SuperApp-RewardReferral/TZTigoSuperAppRewardReferral/Controllers/RewardManagementController.cs › RewardManagementController.RedeemReferrelCode` |
| 6 | `param is string` | branch / error envelope | — | `TZ-Tigo-SuperApp-RewardReferral/TZTigoSuperAppRewardReferral/Controllers/RewardManagementController.cs › RewardManagementController.RedeemReferrelCode` |
| 7 | `_configuration.GetValue<string>("EnableLog:Information"` | branch / error envelope | — | `TZ-Tigo-SuperApp-RewardReferral/TZTigoSuperAppRewardReferral/Controllers/RewardManagementController.cs › RewardManagementController.RedeemReferrelCode` |
| 8 | `param is string` | branch / error envelope | — | `TZ-Tigo-SuperApp-RewardReferral/TZTigoSuperAppRewardReferral/Controllers/RewardManagementController.cs › RewardManagementController.RedeemReferrelCode` |
| 9 | `alreadyRedeemed == false` | branch / error envelope | — | `TZ-Tigo-SuperApp-RewardReferral/TZTigoSuperAppRewardReferral/Controllers/RewardManagementController.cs › RewardManagementController.RedeemReferrelCode` |
| 10 | `referralCode.responseData != null` | branch / error envelope | — | `TZ-Tigo-SuperApp-RewardReferral/TZTigoSuperAppRewardReferral/Controllers/RewardManagementController.cs › RewardManagementController.RedeemReferrelCode` |
| 11 | `referralCode.responseData.expirydate >= DateTime.Now.Date` | branch / error envelope | — | `TZ-Tigo-SuperApp-RewardReferral/TZTigoSuperAppRewardReferral/Controllers/RewardManagementController.cs › RewardManagementController.RedeemReferrelCode` |
| 12 | `limits.responseData == null` | branch / error envelope | — | `TZ-Tigo-SuperApp-RewardReferral/TZTigoSuperAppRewardReferral/Controllers/RewardManagementController.cs › RewardManagementController.RedeemReferrelCode` |
| 13 | `_configuration.GetValue<string>("EnableLog:Information"` | branch / error envelope | — | `TZ-Tigo-SuperApp-RewardReferral/TZTigoSuperAppRewardReferral/Controllers/RewardManagementController.cs › RewardManagementController.RedeemReferrelCode` |
| 14 | `param is string` | branch / error envelope | — | `TZ-Tigo-SuperApp-RewardReferral/TZTigoSuperAppRewardReferral/Controllers/RewardManagementController.cs › RewardManagementController.RedeemReferrelCode` |

## Internal call chain
1. Client POST `/api/RewardManagement/RedeemReferrelCode` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `RedeemReferrelCodeRequest` on `HttpContext.Items['modeldata']`.
3. SessionValidationFilter validates `X-User-Session`.
4. `RewardManagementController.RedeemReferrelCode` runs (`TZ-Tigo-SuperApp-RewardReferral/TZTigoSuperAppRewardReferral/Controllers/RewardManagementController.cs`).
5. Calls `_referrelCodeService.RedeemRefferelCode`.
6. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  participant EncFilter
  App->>EncFilter: POST payload envelope
  EncFilter->>EncFilter: AES decrypt payload
  EncFilter->>RewardManagementController: Items['modeldata']
  participant RewardManagementController
  RewardManagementController->>_logger: LogInformation()
  RewardManagementController->>_referrelCodeService: RedeemRefferelCode()
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
| 500 | 500 | BE-ERR-REWARD-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-REWARD-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-REWARD-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-RewardReferral/TZTigoSuperAppRewardReferral/Controllers/RewardManagementController.cs › RewardManagementController.RedeemReferrelCode` @ `b47cb93`
- Decrypted DTO `RedeemReferrelCodeRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
