---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-336]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---

# BE-API-CONFIG-336 MixxTipInternalController.GetStaffMsisdn
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/Internal/MixxTipInternalController.cs › MixxTipInternalController.GetStaffMsisdn` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/internal/mixxtip/staff/getmsisdn
  internal_path: /api/internal/mixxtip/staff/getmsisdn
  dispatch_field: null
  dispatch_value: null
  controller_action: MixxTipInternalController.GetStaffMsisdn
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/internal/mixxtip/staff/getmsisdn`
- **Auth / filters:** none on action (pipeline may still authorize)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `staffcode` | `string?` | N | — | shape only | staffcode |
| `staffmsisdn` | `string?` | N | — | shape only | staffmsisdn |

Headers / route / query params: none parsed beyond action signature `[('request', 'MixxTipStaffMsisdnRequest')]`

Sample (synthetic):
```json
{
  "staffcode": "<string>",
  "staffmsisdn": "255XXXXXXXXX"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `request == null \|\|                 (string.IsNullOrWhiteSpace(request.staffcode` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/Internal/MixxTipInternalController.cs › MixxTipInternalController.GetStaffMsisdn` |
| 2 | `!result.success` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/Internal/MixxTipInternalController.cs › MixxTipInternalController.GetStaffMsisdn` |
| 3 | `request == null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/Internal/MixxTipInternalController.cs › MixxTipInternalController.GetStaffMsisdn` |
| 4 | `!hasCode && !hasMsisdn` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/Internal/MixxTipInternalController.cs › MixxTipInternalController.GetStaffMsisdn` |
| 5 | `hasCode` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/Internal/MixxTipInternalController.cs › MixxTipInternalController.GetStaffMsisdn` |
| 6 | `hasMsisdn` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/Internal/MixxTipInternalController.cs › MixxTipInternalController.GetStaffMsisdn` |
| 7 | `msisdns.Count == 0` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/Internal/MixxTipInternalController.cs › MixxTipInternalController.GetStaffMsisdn` |
| 8 | `distinctMsisdns.Count > 1` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/Internal/MixxTipInternalController.cs › MixxTipInternalController.GetStaffMsisdn` |

## Internal call chain
1. Client POST `/api/internal/mixxtip/staff/getmsisdn`.
2. `MixxTipInternalController.GetStaffMsisdn` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/Internal/MixxTipInternalController.cs`).
3. Calls `string.IsNullOrWhiteSpace`.
4. Calls `string.IsNullOrWhiteSpace`.
5. Calls `_repo.ResolveStaffTipAsync`.
6. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>MixxTipInternalController: POST /api/internal/mixxtip/staff/getmsisdn
  participant MixxTipInternalController
  MixxTipInternalController->>string: IsNullOrWhiteSpace()
  MixxTipInternalController->>_repo: ResolveStaffTipAsync()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/Internal/MixxTipInternalController.cs › MixxTipInternalController.GetStaffMsisdn` @ `9c00072`
- Decrypted DTO `MixxTipStaffMsisdnRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
