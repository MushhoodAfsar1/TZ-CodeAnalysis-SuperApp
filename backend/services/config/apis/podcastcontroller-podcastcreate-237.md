---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-237]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 9c00072
updated: 2026-10-05
confidence: partial
---

# BE-API-CONFIG-237 PodcastController.PodcastCreate
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/PodcastController.cs › PodcastController.PodcastCreate` · **Conf.:** partial

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Podcast/PodcastCreate
  internal_path: /api/Podcast/PodcastCreate
  dispatch_field: null
  dispatch_value: null
  controller_action: PodcastController.PodcastCreate
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Podcast/PodcastCreate`
- **Auth / filters:** Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| *(none parsed)* | | | | | |

Headers / route / query params: none parsed beyond action signature (no params).

Sample (synthetic):
```json
{}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `!string.IsNullOrEmpty(request.podcasttitleimagefile` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/PodcastController.cs › PodcastController.PodcastCreate` |
| 2 | `!validationResult.IsValid` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/PodcastController.cs › PodcastController.PodcastCreate` |
| 3 | `validationResult.HasWarnings` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/PodcastController.cs › PodcastController.PodcastCreate` |
| 4 | `_configuration.GetValue<string>("EnableLog:Warning"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/PodcastController.cs › PodcastController.PodcastCreate` |

## Internal call chain
1. Client POST `/api/Podcast/PodcastCreate`.
2. `PodcastController.PodcastCreate` runs (`TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/PodcastController.cs`).
3. Calls `User.FindFirst`.
4. Calls `string.IsNullOrEmpty`.
5. Calls `podcasttitleimagefile.Contains`.
6. Calls `podcasttitleimagefile.Contains`.
7. Calls `ImageValidationUploadHelper.ValidateAndUploadAsync`.
8. Calls `this.StatusCode`.
9. Calls `string.Join`.
10. Calls `_loggerMvc.LogWarning`.
11. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>PodcastController: POST /api/Podcast/PodcastCreate
  participant PodcastController
  PodcastController->>User: FindFirst()
  PodcastController->>Value: ToString()
  PodcastController->>string: IsNullOrEmpty()
  PodcastController->>podcasttitleimagefile: Contains()
  PodcastController->>ImageValidationUploadHelper: ValidateAndUploadAsync()
  PodcastController->>string: Join()
  PodcastController->>_loggerMvc: LogWarning()
  PodcastController->>validationWarnings: AddRange()
  PodcastController->>Warnings: Select()
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
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/BO/PodcastController.cs › PodcastController.PodcastCreate` @ `9c00072`

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
