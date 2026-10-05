---
kb_section: backend
type: api-contract
ids: [BE-API-MERCH-013]
service: MERCH
repo: TZ-Tigo-SuperApp-Merchant
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 2367767
updated: 2026-10-05
confidence: confirmed
---
# BE-API-MERCH-013 MerchantController.GenerateQR
**Service:** BE-SVC-MERCH · **Handler:** `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/MerchantController.cs › MerchantController.GenerateQR` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/Merchant
  internal_path: /api/Merchant
  dispatch_field: null
  dispatch_value: null
  controller_action: MerchantController.GenerateQR
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** QRCodeRequest

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| SessionToken | `string?` | no | — | DataAnnotations / action | — |
| QRType | `string?` | no | — | DataAnnotations / action | — |
| QRId | `string?` | no | — | DataAnnotations / action | — |
| EntityOwnerType | `string?` | no | — | DataAnnotations / action | — |
| EntityType | `string?` | no | — | DataAnnotations / action | — |
| EntityName | `string?` | no | — | DataAnnotations / action | — |
| TradedAs | `string?` | no | — | DataAnnotations / action | — |
| SubscriberMsisdn | `string?` | no | — | DataAnnotations / action | — |
| ParentEAN | `string?` | no | — | DataAnnotations / action | — |
| NIN | `string?` | no | — | DataAnnotations / action | — |
| Region | `string?` | no | — | DataAnnotations / action | — |
| District | `string?` | no | — | DataAnnotations / action | — |
| Ward | `string?` | no | — | DataAnnotations / action | — |
| StreetNoAndPlotNo | `string?` | no | — | DataAnnotations / action | — |
| TanzanianPostalCode | `string?` | no | — | DataAnnotations / action | — |
| CountryCode | `string?` | no | — | DataAnnotations / action | — |
| ChannelType | `string?` | no | — | DataAnnotations / action | — |
| RetailerMsisdn | `string?` | no | — | DataAnnotations / action | — |
| RemoteIp | `string?` | no | — | DataAnnotations / action | — |
| Latitude | `string?` | no | — | DataAnnotations / action | — |
| Longitude | `string?` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "SessionToken": "<SessionToken>", "QRType": "<QRType>", "QRId": "<QRId>", "EntityOwnerType": "<EntityOwnerType>", "EntityType": "<EntityType>", "EntityName": "<EntityName>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `MerchantController.GenerateQR`
2. Action body in `TZTigoSuperAppMerchant/Controllers/MerchantController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as MerchantController
  participant Svc as downstream
  App->>Ctrl: POST /api/Merchant
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
| See service data-model | R/W | Traced at SHA 2367767 |

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
See `services/merch/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Merchant/TZTigoSuperAppMerchant/Controllers/MerchantController.cs › MerchantController.GenerateQR` @ `2367767`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
