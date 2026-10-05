---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-368]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-368 MerchantManagementAppController.UpdatePrivileges
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/MerchantManagementAppController.cs › MerchantManagementAppController.UpdatePrivileges` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/MerchantManagementApp/UpdatePrivileges
  internal_path: /api/MerchantManagementApp/UpdatePrivileges
  dispatch_field: null
  dispatch_value: null
  controller_action: MerchantManagementAppController.UpdatePrivileges
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/MerchantManagementApp/UpdatePrivileges`
- **Auth / filters:** SessionValidationFilter (X-User-Session), EncryptionProviderFilter<MerchantRequestDto>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `MerchantRequestDto`

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `requestingOrganisationTransactionReference` | `string?` | N | — | shape only | requestingOrganisationTransactionReference |
| `merchantmsisdn` | `string` | N | — | shape only | merchantmsisdn |
| `usermsisdn` | `string` | N | — | shape only | usermsisdn |
| `options` | `List<Option>?` | N | — | shape only | options |
| `country` | `string?` | N | — | shape only | country |
| `notificationnumber` | `string?` | N | — | shape only | notificationnumber |
| `language` | `string?` | N | — | shape only | language |
| `requestId` | `string?` | N | — | shape only | requestId |

Headers / route / query params: none parsed beyond action signature `[('msg', 'RequestModel')]`

Sample (synthetic):
```json
{"payload": "<ciphertext-or-json>"}
# decrypted payload:
{
  "requestingOrganisationTransactionReference": "<string>",
  "merchantmsisdn": "255XXXXXXXXX",
  "usermsisdn": "255XXXXXXXXX",
  "options": [],
  "country": "<string>",
  "notificationnumber": "<string>",
  "language": "<string>",
  "requestId": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt `payload` with AES when config `is_encrypted`/`isEncrypted` is true; else JSON-deserialize | Filter stores raw string; later cast may fail → 500 | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/MerchantManagementAppController.cs › MerchantManagementAppController.UpdatePrivileges` |
| 2 | Validate `X-User-Session` JWT (`TokenKey`) then Redis/DB token | HTTP 410 envelope | BE-BR-CONFIG-001 | `TZ-Tigo-SuperApp-Configuration › SessionValidationFilter` |
| 3 | `retdata.success == true` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/MerchantManagementAppController.cs › MerchantManagementAppController.UpdatePrivileges` |
| 4 | `merchantAppReques.options.Any(` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/MerchantManagementAppController.cs › MerchantManagementAppController.UpdatePrivileges` |
| 5 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/MerchantManagementAppController.cs › MerchantManagementAppController.UpdatePrivileges` |
| 6 | `_configuration.GetValue<string>("EnableLog:Debug"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/MerchantManagementAppController.cs › MerchantManagementAppController.UpdatePrivileges` |
| 7 | `_configuration.GetValue<string>("EnableLog:Error"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/MerchantManagementAppController.cs › MerchantManagementAppController.UpdatePrivileges` |

## Internal call chain
1. Client POST `/api/MerchantManagementApp/UpdatePrivileges` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `MerchantRequestDto` on `HttpContext.Items['modeldata']`.
3. SessionValidationFilter validates `X-User-Session`.
4. `MerchantManagementAppController.UpdatePrivileges` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/MerchantManagementAppController.cs`).
5. Calls `_merchantManagementRepository.UpdatePrivileges`.
6. Calls `_logger.LogDebug`.
7. Calls `MethodBase.GetCurrentMethod`.
8. Calls `MethodBase.GetCurrentMethod`.
9. Calls `Diagnostics.StackFrame`.
10. Calls `this.StatusCode`.
11. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  participant EncFilter
  App->>EncFilter: POST payload envelope
  EncFilter->>EncFilter: AES decrypt payload
  EncFilter->>MerchantManagementAppController: Items['modeldata']
  participant MerchantManagementAppController
  MerchantManagementAppController->>_merchantManagementRepository: UpdatePrivileges()
  MerchantManagementAppController->>_logger: LogDebug()
  MerchantManagementAppController->>MethodBase: GetCurrentMethod()
  MerchantManagementAppController->>Diagnostics: StackFrame()
  MerchantManagementAppController->>_logger: LogError()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/MerchantManagementAppController.cs › MerchantManagementAppController.UpdatePrivileges` @ `9c00072`
- Decrypted DTO `MerchantRequestDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
