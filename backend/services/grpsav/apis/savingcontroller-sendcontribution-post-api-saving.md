---
kb_section: backend
type: api-contract
ids: [BE-API-GRPSAV-011]
service: GRPSAV
repo: TZ-Tigo-SuperApp-GroupSaving
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: ed4ac20
updated: 2026-10-05
confidence: confirmed
---
# BE-API-GRPSAV-011 SavingController.SendContribution
**Service:** BE-SVC-GRPSAV · **Handler:** `TZ-Tigo-SuperApp-GroupSaving/TZTigoSuperAppGroupSaving/Controllers/SavingController.cs › SavingController.SendContribution` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Saving
  internal_path: /api/Saving
  dispatch_field: null
  dispatch_value: null
  controller_action: SavingController.SendContribution
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** SendContributionRequest

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| groupId | `string?` | no | — | DataAnnotations / action | — |
| phoneNumber | `string?` | no | — | DataAnnotations / action | — |
| amount | `string?` | no | — | DataAnnotations / action | — |
| forOthers | `string?` | no | — | DataAnnotations / action | — |
| bParty | `string?` | no | — | DataAnnotations / action | — |
| receipt | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "groupId": "<groupId>", "phoneNumber": "<phoneNumber>", "amount": "<amount>", "forOthers": "<forOthers>", "bParty": "<bParty>", "receipt": "<receipt>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `SavingController.SendContribution`
2. Action body in `TZTigoSuperAppGroupSaving/Controllers/SavingController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as SavingController
  participant Svc as downstream
  App->>Ctrl: POST /api/Saving
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
| See service data-model | R/W | Traced at SHA ed4ac20 |

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
See `services/grpsav/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-GroupSaving/TZTigoSuperAppGroupSaving/Controllers/SavingController.cs › SavingController.SendContribution` @ `ed4ac20`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
