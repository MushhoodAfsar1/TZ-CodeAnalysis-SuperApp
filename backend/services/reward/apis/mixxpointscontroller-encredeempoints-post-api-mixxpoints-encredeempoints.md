---
kb_section: backend
type: api-contract
ids: [BE-API-REWARD-019]
service: REWARD
repo: TZ-Tigo-SuperApp-RewardReferral
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: b47cb93
updated: 2026-10-05
confidence: confirmed
---
# BE-API-REWARD-019 MixxPointsController.encRedeemPoints
**Service:** BE-SVC-REWARD · **Handler:** `TZ-Tigo-SuperApp-RewardReferral/TZTigoSuperAppRewardReferral/Controllers/MixxPointsController.cs › MixxPointsController.encRedeemPoints` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/MixxPoints/encRedeemPoints
  internal_path: /api/MixxPoints/encRedeemPoints
  dispatch_field: null
  dispatch_value: null
  controller_action: MixxPointsController.encRedeemPoints
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** none on this action

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| CustomerMsisdn | `string?` | no | — | DataAnnotations / action | — |
| RedeemType | `string?` | no | — | DataAnnotations / action | — |
| RedeemProductValue | `string?` | no | — | DataAnnotations / action | — |
| PointsValue | `string?` | no | — | DataAnnotations / action | — |
| ReferenceId | `string?` | no | — | DataAnnotations / action | — |
| Pin | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "CustomerMsisdn": "<CustomerMsisdn>", "RedeemType": "<RedeemType>", "RedeemProductValue": "<RedeemProductValue>", "PointsValue": "<PointsValue>", "ReferenceId": "<ReferenceId>", "Pin": "<Pin>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `MixxPointsController.encRedeemPoints`
2. Action body in `TZTigoSuperAppRewardReferral/Controllers/MixxPointsController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as MixxPointsController
  participant Svc as downstream
  App->>Ctrl: POST /api/MixxPoints/encRedeemPoints
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
| See service data-model | R/W | Traced at SHA b47cb93 |

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
See `services/reward/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-RewardReferral/TZTigoSuperAppRewardReferral/Controllers/MixxPointsController.cs › MixxPointsController.encRedeemPoints` @ `b47cb93`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
