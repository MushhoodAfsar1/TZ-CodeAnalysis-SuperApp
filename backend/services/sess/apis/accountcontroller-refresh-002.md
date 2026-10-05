---
kb_section: backend
type: api-contract
ids: [BE-API-SESS-002]
service: SESS
repo: TZ-Tigo-SuperApp-Session
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 6f24061
updated: 2026-10-05
confidence: confirmed
---

# BE-API-SESS-002 AccountController.Refresh
**Service:** BE-SVC-SESS · **Handler:** `TZ-Tigo-SuperApp-Session/TZTigoSuperAppSession/Controllers/AccountController.cs › AccountController.Refresh` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Account/refreshToken
  internal_path: /api/Account/refreshToken
  dispatch_field: null
  dispatch_value: null
  controller_action: AccountController.Refresh
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Account/refreshToken`
- **Auth / filters:** EncryptionProviderFilter<RefreshTokenDto>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `RefreshTokenDto`

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `requestingOrganisationTransactionReference` | `string` | N | — | shape only | requestingOrganisationTransactionReference |
| `iPInfo` | `string` | N | — | shape only | iPInfo |
| `geoCode` | `string` | N | — | shape only | geoCode |
| `useCaseName` | `string` | N | — | shape only | useCaseName |
| `channel` | `string` | N | — | shape only | channel |
| `appVersion` | `string` | N | — | shape only | appVersion |
| `languageCode` | `string` | N | — | shape only | languageCode |
| `deviceId` | `string` | N | — | shape only | deviceId |
| `deviceMaker` | `string` | N | — | shape only | deviceMaker |
| `oS` | `string` | N | — | shape only | oS |
| `accesstoken` | `string` | N | — | shape only | accesstoken |
| `msisdn` | `string` | N | — | shape only | msisdn |
| `accesstoken` | `string` | N | — | shape only | accesstoken |
| `refreshtoken` | `string` | N | — | shape only | refreshtoken |

Headers / route / query params: none parsed beyond action signature `[('msg', 'RequestModel')]`

Sample (synthetic):
```json
{"payload": "<ciphertext-or-json>"}
# decrypted payload:
{
  "requestingOrganisationTransactionReference": "<string>",
  "iPInfo": "<encrypted-pin>",
  "geoCode": "<string>",
  "useCaseName": "<string>",
  "channel": "<string>",
  "appVersion": "<string>",
  "languageCode": "<string>",
  "deviceId": "<device-id>",
  "deviceMaker": "<string>",
  "oS": "<string>",
  "accesstoken": "<jwt>",
  "msisdn": "255XXXXXXXXX",
  "accesstoken": "<jwt>",
  "refreshtoken": "<jwt>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt `payload` with AES when config `is_encrypted`/`isEncrypted` is true; else JSON-deserialize | Filter stores raw string; later cast may fail → 500 | — | `TZ-Tigo-SuperApp-Session/TZTigoSuperAppSession/Controllers/AccountController.cs › AccountController.Refresh` |
| 2 | `accessToken == null \|\| accessToken == "False"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Session/TZTigoSuperAppSession/Controllers/AccountController.cs › AccountController.Refresh` |
| 3 | `_configuration.GetValue<string>("EnableLog:Information"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Session/TZTigoSuperAppSession/Controllers/AccountController.cs › AccountController.Refresh` |
| 4 | `_configuration.GetValue<string>("EnableLog:Information"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Session/TZTigoSuperAppSession/Controllers/AccountController.cs › AccountController.Refresh` |
| 5 | `_configuration.GetValue<string>("EnableLog:Information"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Session/TZTigoSuperAppSession/Controllers/AccountController.cs › AccountController.Refresh` |
| 6 | `jwtSecurityToken == null \|\| !jwtSecurityToken.Header.Alg.Equals(SecurityAlgorithms.HmacSha256, StringComparison.InvariantCultureIgnoreCase` | branch / error envelope | — | `TZ-Tigo-SuperApp-Session/TZTigoSuperAppSession/Controllers/AccountController.cs › AccountController.Refresh` |

## Internal call chain
1. Client POST `/api/Account/refreshToken` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `RefreshTokenDto` on `HttpContext.Items['modeldata']`.
3. `AccountController.Refresh` runs (`TZ-Tigo-SuperApp-Session/TZTigoSuperAppSession/Controllers/AccountController.cs`).
4. Calls `JsonConvert.SerializeObject`.
5. Calls `Headers.TryGetValue`.
6. Calls `this.StatusCode`.
7. Calls `UTF8.GetBytes`.
8. Calls `_configuration.GetSection`.
9. Calls `accesstoken.Replace`.
10. Calls `Utilities.GetPrincipalFromExpiredToken`.
11. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  participant EncFilter
  App->>EncFilter: POST payload envelope
  EncFilter->>EncFilter: AES decrypt payload
  EncFilter->>AccountController: Items['modeldata']
  participant AccountController
  AccountController->>_logger: LogInformation()
  AccountController->>Headers: TryGetValue()
  AccountController->>UTF8: GetBytes()
  AccountController->>_configuration: GetSection()
  AccountController->>accesstoken: Replace()
  AccountController->>Utilities: GetPrincipalFromExpiredToken()
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
| 500 | 500 | BE-ERR-SESS-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-SESS-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-SESS-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-Session/TZTigoSuperAppSession/Controllers/AccountController.cs › AccountController.Refresh` @ `6f24061`
- Decrypted DTO `RefreshTokenDto` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
