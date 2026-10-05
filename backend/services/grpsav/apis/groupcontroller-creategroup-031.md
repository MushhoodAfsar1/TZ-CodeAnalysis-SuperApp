---
kb_section: backend
type: api-contract
ids: [BE-API-GRPSAV-031]
service: GRPSAV
repo: TZ-Tigo-SuperApp-GroupSaving
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: ed4ac20
updated: 2026-10-05
confidence: confirmed
---

# BE-API-GRPSAV-031 GroupController.CreateGroup
**Service:** BE-SVC-GRPSAV · **Handler:** `TZ-Tigo-SuperApp-GroupSaving/TZTigoSuperAppGroupSaving/Controllers/GroupController.cs › GroupController.CreateGroup` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Group/CreateGroup
  internal_path: /api/Group/CreateGroup
  dispatch_field: null
  dispatch_value: null
  controller_action: GroupController.CreateGroup
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Group/CreateGroup`
- **Auth / filters:** EncryptionProviderFilter<CreateGroupRequest>
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
Wire envelope (encrypted or plaintext JSON string in `payload`). Table below is the **decrypted** DTO bound after the filter.

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `payload` | string | Y | AES ciphertext or JSON | `RequestModel` | whole-body envelope |

**Decrypted type:** `CreateGroupRequest`

| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `requestingOrganisationTransactionReference` | `string?` | N | — | shape only | requestingOrganisationTransactionReference |
| `requestId` | `string?` | N | — | shape only | requestId |
| `channel` | `string?` | N | — | shape only | channel |
| `ipInfo` | `string?` | N | — | shape only | ipInfo |
| `appVersion` | `string?` | N | — | shape only | appVersion |
| `languageCode` | `string?` | N | — | shape only | languageCode |
| `deviceId` | `string?` | N | — | shape only | deviceId |
| `deviceType` | `string?` | N | — | shape only | deviceType |
| `pushId` | `string?` | N | — | shape only | pushId |
| `deviceMaker` | `string?` | N | — | shape only | deviceMaker |
| `oS` | `string?` | N | — | shape only | oS |
| `geoCode` | `string?` | N | — | shape only | geoCode |
| `userCaseName` | `string?` | N | — | shape only | userCaseName |
| `accessToken` | `string?` | N | — | shape only | accessToken |
| `groupName` | `string?` | N | — | shape only | groupName |
| `amount` | `string?` | N | — | shape only | amount |
| `groupType` | `string?` | N | — | shape only | groupType |
| `phoneNumber` | `string?` | N | — | shape only | phoneNumber |
| `firstName` | `string?` | N | — | shape only | firstName |
| `familyName` | `string?` | N | — | shape only | familyName |
| `receipt` | `string?` | N | — | shape only | receipt |
| `dob` | `DateTime?` | N | — | shape only | dob |
| `network` | `string?` | N | — | shape only | network |
| `language` | `string?` | N | — | shape only | language |

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
  "deviceType": "<string>",
  "pushId": "<push-token>",
  "deviceMaker": "<string>",
  "oS": "<string>",
  "geoCode": "<string>",
  "userCaseName": "<string>",
  "accessToken": "<jwt>",
  "groupName": "<string>",
  "amount": "<amount>",
  "groupType": "<string>",
  "phoneNumber": "255XXXXXXXXX",
  "firstName": "<string>",
  "familyName": "<string>",
  "receipt": "<string>",
  "dob": "<iso-datetime>",
  "network": "<string>",
  "language": "<string>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | Decrypt `payload` with AES when config `is_encrypted`/`isEncrypted` is true; else JSON-deserialize | Filter stores raw string; later cast may fail → 500 | — | `TZ-Tigo-SuperApp-GroupSaving/TZTigoSuperAppGroupSaving/Controllers/GroupController.cs › GroupController.CreateGroup` |
| 2 | `result != null && result.code == "0"` | branch / error envelope | — | `TZ-Tigo-SuperApp-GroupSaving/TZTigoSuperAppGroupSaving/Controllers/GroupController.cs › GroupController.CreateGroup` |
| 3 | `_configuration.GetValue<string>("EnableLog:Error"` | branch / error envelope | — | `TZ-Tigo-SuperApp-GroupSaving/TZTigoSuperAppGroupSaving/Controllers/GroupController.cs › GroupController.CreateGroup` |

## Internal call chain
1. Client POST `/api/Group/CreateGroup` with `{ payload }` envelope.
2. Encryption filter decrypts payload into `CreateGroupRequest` on `HttpContext.Items['modeldata']`.
3. `GroupController.CreateGroup` runs (`TZ-Tigo-SuperApp-GroupSaving/TZTigoSuperAppGroupSaving/Controllers/GroupController.cs`).
4. Calls `_groupService.CreateGroup`.
5. Calls `_apiResponseHandler.CreateResponse`.
6. Calls `_apiResponseHandler.CreateResponse`.
7. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  participant EncFilter
  App->>EncFilter: POST payload envelope
  EncFilter->>EncFilter: AES decrypt payload
  EncFilter->>GroupController: Items['modeldata']
  participant GroupController
  GroupController->>_groupService: CreateGroup()
  GroupController->>_apiResponseHandler: CreateResponse()
  GroupController->>_logger: LogError()
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
| 500 | 500 | BE-ERR-GRPSAV-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-GRPSAV-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-GRPSAV-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-GroupSaving/TZTigoSuperAppGroupSaving/Controllers/GroupController.cs › GroupController.CreateGroup` @ `ed4ac20`
- Decrypted DTO `CreateGroupRequest` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
