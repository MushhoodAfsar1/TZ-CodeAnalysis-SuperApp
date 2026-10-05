---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-264]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-264 MerchantController.UpdateAsync
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MerchantController.cs › MerchantController.UpdateAsync` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Merchant/update
  internal_path: /api/Merchant/update
  dispatch_field: null
  dispatch_value: null
  controller_action: MerchantController.UpdateAsync
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Merchant/update`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `addressLine` | `string?` | N | — | shape only | addressLine |
| `createdBy` | `object?` | N | — | shape only | createdBy |
| `fridayScheduleFrom` | `string?` | N | — | shape only | fridayScheduleFrom |
| `fridayScheduleTo` | `string?` | N | — | shape only | fridayScheduleTo |
| `id` | `int?` | N | — | shape only | id |
| `latitude` | `string?` | N | — | shape only | latitude |
| `locality` | `string?` | N | — | shape only | locality |
| `longitude` | `string?` | N | — | shape only | longitude |
| `mondayScheduleFrom` | `string?` | N | — | shape only | mondayScheduleFrom |
| `mondayScheduleTo` | `string?` | N | — | shape only | mondayScheduleTo |
| `nameOfEstablishment` | `string?` | N | — | shape only | nameOfEstablishment |
| `phoneNumber` | `string?` | N | — | shape only | phoneNumber |
| `region` | `string?` | N | — | shape only | region |
| `saturdayScheduleFrom` | `string?` | N | — | shape only | saturdayScheduleFrom |
| `saturdayScheduleTo` | `string?` | N | — | shape only | saturdayScheduleTo |
| `sundayScheduleFrom` | `string?` | N | — | shape only | sundayScheduleFrom |
| `sundayScheduleTo` | `string?` | N | — | shape only | sundayScheduleTo |
| `thursdayScheduleFrom` | `string?` | N | — | shape only | thursdayScheduleFrom |
| `thursdayScheduleTo` | `string?` | N | — | shape only | thursdayScheduleTo |
| `tuesdayScheduleFrom` | `string?` | N | — | shape only | tuesdayScheduleFrom |
| `tuesdayScheduleTo` | `string?` | N | — | shape only | tuesdayScheduleTo |
| `updatedBy` | `object?` | N | — | shape only | updatedBy |
| `wednesdayScheduleFrom` | `string?` | N | — | shape only | wednesdayScheduleFrom |
| `wednesdayScheduleTo` | `string?` | N | — | shape only | wednesdayScheduleTo |

Headers / route / query params: none parsed beyond action signature `[('merchantDto', 'merchantUpdateDto')]`

Sample (synthetic):
```json
{
  "addressLine": "<string>",
  "createdBy": "<string>",
  "fridayScheduleFrom": "<string>",
  "fridayScheduleTo": "<string>",
  "id": 0,
  "latitude": "<lat>",
  "locality": "<string>",
  "longitude": "<lng>",
  "mondayScheduleFrom": "<string>",
  "mondayScheduleTo": "<string>",
  "nameOfEstablishment": "<string>",
  "phoneNumber": "255XXXXXXXXX",
  "region": "<string>",
  "saturdayScheduleFrom": "<string>",
  "saturdayScheduleTo": "<string>",
  "sundayScheduleFrom": "<string>",
  "sundayScheduleTo": "<string>",
  "thursdayScheduleFrom": "<string>",
  "thursdayScheduleTo": "<string>",
  "tuesdayScheduleFrom": "<string>",
  "tuesdayScheduleTo": "<string>",
  "updatedBy": "<string>",
  "wednesdayScheduleFrom": "<string>",
  "wednesdayScheduleTo": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `merchanttoUpdate == null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MerchantController.cs › MerchantController.UpdateAsync` |
| 2 | `_configuration.GetValue<string>("EnableLog:Information"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MerchantController.cs › MerchantController.UpdateAsync` |

## Internal call chain
1. Client POST `/api/Merchant/update`.
2. `MerchantController.UpdateAsync` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MerchantController.cs`).
3. Calls `string.Format`.
4. Calls `merchant.FirstOrDefault`.
5. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>MerchantController: POST /api/Merchant/update
  participant MerchantController
  MerchantController->>_logger: LogInformation()
  MerchantController->>string: Format()
  MerchantController->>merchant: FirstOrDefault()
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
| 500 | 500 | BE-ERR-CONFIG-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-CONFIG-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-CONFIG-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MerchantController.cs › MerchantController.UpdateAsync` @ `9c00072`
- Decrypted DTO `merchantUpdateDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
