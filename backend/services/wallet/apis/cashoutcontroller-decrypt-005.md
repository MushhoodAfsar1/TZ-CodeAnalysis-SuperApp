---
kb_section: backend
type: api-contract
ids: [BE-API-WALLET-005]
service: WALLET
repo: TZ-Tigo-SuperApp-Wallet
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 27737b1
updated: 2026-10-05
confidence: confirmed
---

# BE-API-WALLET-005 CashOutController.Decrypt
**Service:** BE-SVC-WALLET · **Handler:** `TZ-Tigo-SuperApp-Wallet/TZTigoSuperAppWallet/Controllers/CashOutController.cs › CashOutController.Decrypt` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/CashOut/decrypt
  internal_path: /api/CashOut/decrypt
  dispatch_field: null
  dispatch_value: null
  controller_action: CashOutController.Decrypt
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/CashOut/decrypt`
- **Auth / filters:** none on action (pipeline may still authorize)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| *(none parsed)* | | | | | |

Headers / route / query params: none parsed beyond action signature `[('data', 'String')]`

Sample (synthetic):
```json
{}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | No explicit guard parsed in action body | — | — | static parse |

## Internal call chain
1. Client POST `/api/CashOut/decrypt`.
2. `CashOutController.Decrypt` runs (`TZ-Tigo-SuperApp-Wallet/TZTigoSuperAppWallet/Controllers/CashOutController.cs`).
3. Calls `RequestSecurity.Decrypt`.
4. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>CashOutController: POST /api/CashOut/decrypt
  participant CashOutController
  CashOutController->>RequestSecurity: Decrypt()
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
| 500 | 500 | BE-ERR-WALLET-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-WALLET-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-WALLET-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-Wallet/TZTigoSuperAppWallet/Controllers/CashOutController.cs › CashOutController.Decrypt` @ `27737b1`

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
