---
kb_section: backend
type: api-contract
ids: [BE-API-IDENT-025]
service: IDENT
repo: TZ-Tigo-SuperApp-Identity
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: e7397b0
updated: 2026-10-05
confidence: confirmed
---

# BE-API-IDENT-025 AccountController.passwordchange
**Service:** BE-SVC-IDENT · **Handler:** `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.passwordchange` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Account/passwordchange
  internal_path: /api/Account/passwordchange
  dispatch_field: null
  dispatch_value: null
  controller_action: AccountController.passwordchange
  topic: null
```

## Exposure & security
- **Method / path:** `POST /api/Account/passwordchange`
- **Auth / filters:** AllowAnonymous, Authorize (JWT)
- **Headers:** `X-User-Session` (Bearer JWT) when session filter present; `Content-Type: application/json`.
- **Encryption:** whole-body AES on `payload` / response when enabled (`is_encrypted` or `isEncrypted`). Mechanism only; keys not documented.

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| `userName` | `string?` | N | — | shape only | userName |
| `CurrentPassword` | `string?` | N | — | shape only | CurrentPassword |
| `NewPassword` | `string?` | N | — | shape only | NewPassword |
| `ConfirmPassword` | `string?` | N | — | shape only | ConfirmPassword |

Headers / route / query params: none parsed beyond action signature `[('passwordChangeRequest', 'PasswordChangeRequestDro')]`

Sample (synthetic):
```json
{
  "userName": "<string>",
  "CurrentPassword": "<password>",
  "NewPassword": "<password>",
  "ConfirmPassword": "<password>"
}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | `user == null` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.passwordchange` |
| 2 | `<condition on identity/token validity>` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.passwordchange` |
| 3 | `signInResult.Succeeded` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.passwordchange` |
| 4 | `result.Succeeded` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.passwordchange` |
| 5 | `_configuration.GetValue<string>("EnableLog:Information"` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.passwordchange` |
| 6 | `param is string` | branch / error envelope | — | `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.passwordchange` |

## Internal call chain
1. Client POST `/api/Account/passwordchange`.
2. `AccountController.passwordchange` runs (`TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs`).
3. Calls `JsonConvert.SerializeObject`.
4. Calls `_userManager.FindByNameAsync`.
5. Calls `_signInManager.CheckPasswordSignInAsync`.
6. Calls `_signInManager.SignOutAsync`.
7. Calls `_userManager.GeneratePasswordResetTokenAsync`.
8. Calls `_userManager.ResetPasswordAsync`.
9. Calls `_signInManager.CheckPasswordSignInAsync`.
10. Returns via `ApiResponseHandler.CreateResponse` or action result; filter may AES-encrypt whole response.

```mermaid
sequenceDiagram
  participant App
  App->>AccountController: POST /api/Account/passwordchange
  participant AccountController
  AccountController->>_logger: LogInformation()
  AccountController->>_userManager: FindByNameAsync()
  AccountController->>_signInManager: CheckPasswordSignInAsync()
  AccountController->>_signInManager: SignOutAsync()
  AccountController->>_userManager: GeneratePasswordResetTokenAsync()
  AccountController->>_userManager: ResetPasswordAsync()
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
| 500 | 500 | BE-ERR-IDENT-001 | unhandled exception in action | Internal Server Error | yes (idempotent GETs only) |
| (session) | 410 | BE-ERR-IDENT-002 | invalid/expired `X-User-Session` | session filter envelope | no (re-auth) |
| mapped | 400/200/201 | — | handler `BaseResponse.success` | CONFIG response-code catalogue | depends |

## Side effects
- Possible audit publish via RabbitMQ `IAuditLogsService` in encryption filter (service-dependent).
- Possible FCM via `IFCMService` when the handler calls it.

## Business rules (links)
- Session validity: `BE-BR-IDENT-001` (when session filter present).

## Config keys
- `is_encrypted` or `isEncrypted` (toggle)
- `responseChanel`, `serviceName` / `Tanzania:serviceName` (message mapping)
- `TokenKey` (JWT validation; value not recorded)

## Evidence
- `TZ-Tigo-SuperApp-Identity/TZTigoSuperAppIdentity/Controllers/AccountController.cs › AccountController.passwordchange` @ `e7397b0`
- Decrypted DTO `PasswordChangeRequestDro` properties from type index.

## Open questions
- Public path may be rewritten by an external gateway not in this repo set.
