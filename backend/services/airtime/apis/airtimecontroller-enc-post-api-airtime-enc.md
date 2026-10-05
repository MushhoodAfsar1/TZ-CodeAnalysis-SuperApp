---
kb_section: backend
type: api-contract
ids: [BE-API-AIRTIME-009]
service: AIRTIME
repo: TZ-Tigo-SuperApp-AirTimeTopup
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 7a52359
updated: 2026-10-05
confidence: confirmed
---
# BE-API-AIRTIME-009 AirTimeController.enc
**Service:** BE-SVC-AIRTIME · **Handler:** `TZ-Tigo-SuperApp-AirTimeTopup/TZTigoSuperAppAirTimeTopup/Controllers/AirTimeController.cs › AirTimeController.enc` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/AirTime/enc
  internal_path: /api/AirTime/enc
  dispatch_field: null
  dispatch_value: null
  controller_action: AirTimeController.enc
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| consumerID | `string?` | no | — | DataAnnotations / action | — |
| transactionID | `string?` | no | — | DataAnnotations / action | — |
| country | `string?` | no | — | DataAnnotations / action | — |
| correlationID | `string?` | no | — | DataAnnotations / action | — |
| sourceMsisdn | `string?` | no | — | DataAnnotations / action | — |
| targetMsisdn | `string?` | no | — | DataAnnotations / action | — |
| pin | `string?` | no | — | DataAnnotations / action | — |
| providerSource | `string?` | no | — | DataAnnotations / action | — |
| providerTarget | `string?` | no | — | DataAnnotations / action | — |
| walletSource | `string?` | no | — | DataAnnotations / action | — |
| walletTarget | `int` | no | — | DataAnnotations / action | — |
| amount | `int` | no | — | DataAnnotations / action | — |
| shortCode | `string?` | no | — | DataAnnotations / action | — |
| operatorName | `string?` | no | — | DataAnnotations / action | — |
| overDraftBrandId | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "consumerID": "<consumerID>", "transactionID": "<transactionID>", "country": "<country>", "correlationID": "<correlationID>", "sourceMsisdn": "<sourceMsisdn>", "targetMsisdn": "<targetMsisdn>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `AirTimeController.enc`
2. Action body in `TZTigoSuperAppAirTimeTopup/Controllers/AirTimeController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as AirTimeController
  participant Svc as downstream
  App->>Ctrl: POST /api/AirTime/enc
  Ctrl->>Svc: business calls
  Svc-->>Ctrl: result
  Ctrl-->>App: envelope
```

## Downstream
| Order | Target (BE-API / BE-INT / BE-EVT) | Sync/Async | Condition | Sent / used fields |
|---|---|---|---|---|
| 1 | In-process services / EF / cache | Sync | always | see call chain |

## Data touched
| Entity / table / SP | R/W | Notes |
|---|---|---|
| See service data-model | R/W | Traced at SHA 7a52359 |

## Response (decrypted)
| Field (JSON) | Type | Always / when | Meaning |
|---|---|---|---|
| success | bool | typical | Operation flag |
| responseCode / responseMessage_* | string | typical | Envelope |
| Data / responseData | object | on success | Payload |

Sample (synthetic):
```json
{ "success": true, "responseCode": "00", "Data": {} }
```

## Errors
| BE code | HTTP | ID | Condition | Message key/text | Retryable |
|---|---|---|---|---|---|
| — | 500 | — | Unhandled exception | Internal error | no |


## Side effects
Documented when the action writes users, tokens, OTP, cache, or audit. See service files.

## Business rules (links)
See `services/airtime/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-AirTimeTopup/TZTigoSuperAppAirTimeTopup/Controllers/AirTimeController.cs › AirTimeController.enc` @ `7a52359`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
