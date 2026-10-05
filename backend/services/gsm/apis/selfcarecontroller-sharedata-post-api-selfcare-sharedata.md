---
kb_section: backend
type: api-contract
ids: [BE-API-GSM-005]
service: GSM
repo: TZ-Tigo-SuperApp-GSM
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 13fe724
updated: 2026-10-05
confidence: confirmed
---
# BE-API-GSM-005 SelfCareController.ShareData
**Service:** BE-SVC-GSM · **Handler:** `TZ-Tigo-SuperApp-GSM/TZTigoSuperAppGSM/Controllers/SelfCareController.cs › SelfCareController.ShareData` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/SelfCare/ShareData
  internal_path: /api/SelfCare/ShareData
  dispatch_field: null
  dispatch_value: null
  controller_action: SelfCareController.ShareData
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** ShareDataRequest

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| USSDDynMenuRequest | `USSDDataMenuRequest?` | no | — | DataAnnotations / action | — |
| param | `List<ShareDataParam>?` | no | — | DataAnnotations / action | — |
| id | `string?` | no | — | DataAnnotations / action | — |
| value | `string?` | no | — | DataAnnotations / action | — |
| ccmsisdn | `string?` | no | — | DataAnnotations / action | — |
| starCode | `string?` | no | — | DataAnnotations / action | — |
| featureId | `string?` | no | — | DataAnnotations / action | — |
| keyWord | `string?` | no | — | DataAnnotations / action | — |
| dataset | `ShareDataset?` | no | — | DataAnnotations / action | — |
| Amount | `string?` | no | — | DataAnnotations / action | — |
| timeStamp | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "USSDDynMenuRequest": "<USSDDynMenuRequest>", "param": "<param>", "id": "<id>", "value": "<value>", "ccmsisdn": "<ccmsisdn>", "starCode": "<starCode>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `SelfCareController.ShareData`
2. Action body in `TZTigoSuperAppGSM/Controllers/SelfCareController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as SelfCareController
  participant Svc as downstream
  App->>Ctrl: POST /api/SelfCare/ShareData
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
| See service data-model | R/W | Traced at SHA 13fe724 |

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
See `services/gsm/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-GSM/TZTigoSuperAppGSM/Controllers/SelfCareController.cs › SelfCareController.ShareData` @ `13fe724`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
