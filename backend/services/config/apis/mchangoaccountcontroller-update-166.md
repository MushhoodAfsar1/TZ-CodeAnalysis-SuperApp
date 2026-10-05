---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-166]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-166 MchangoAccountController.Update
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MchangoAccountController.cs › MchangoAccountController.Update` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/MchangoAccount/update
  internal_path: /api/MchangoAccount/update
  dispatch_field: null
  dispatch_value: null
  controller_action: MchangoAccountController.Update
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/MchangoAccount/update`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `id` | `int` | N | — | shape only | id |
| `numberofaccounts` | `string?` | N | — | shape only | numberofaccounts |
| `bankpartnerid` | `string?` | N | — | shape only | bankpartnerid |
| `bankpartnername` | `string?` | N | — | shape only | bankpartnername |
| `createdby` | `string?` | N | — | shape only | createdby |
| `createddate` | `DateTime?` | N | — | shape only | createddate |
| `updatedby` | `string?` | N | — | shape only | updatedby |
| `updateddate` | `DateTime?` | N | — | shape only | updateddate |

Headers / route / query params: none parsed beyond action signature `[('request', 'MchangoAccountDTO')]`

Sample (synthetic):
```json
{
  "id": 0,
  "numberofaccounts": "<string>",
  "bankpartnerid": "<string>",
  "bankpartnername": "<string>",
  "createdby": "<string>",
  "createddate": "<iso-datetime>",
  "updatedby": "<string>",
  "updateddate": "<iso-datetime>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `subCategory == null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MchangoAccountController.cs › MchangoAccountController.Update` |

## Internal call chain
1. Client POST `/api/MchangoAccount/update`.
2. `MchangoAccountController.Update` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MchangoAccountController.cs`).
3. Calls `User.FindFirst`.
4. Calls `_mchangoAccountRepository.UpdateAsync`.
5. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>MchangoAccountController: POST /api/MchangoAccount/update
  participant MchangoAccountController
  MchangoAccountController->>User: FindFirst()
  MchangoAccountController->>Value: ToString()
  MchangoAccountController->>_mchangoAccountRepository: UpdateAsync()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/MchangoAccountController.cs › MchangoAccountController.Update` @ `9c00072`
- Decrypted DTO `MchangoAccountDTO` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
