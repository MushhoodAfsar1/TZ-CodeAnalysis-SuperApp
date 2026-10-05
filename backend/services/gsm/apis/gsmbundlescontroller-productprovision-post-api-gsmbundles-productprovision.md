---
kb_section: backend
type: api-contract
ids: [BE-API-GSM-009]
service: GSM
repo: TZ-Tigo-SuperApp-GSM
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 13fe724
updated: 2026-10-05
confidence: confirmed
---
# BE-API-GSM-009 GSMBundlesController.ProductProvision
**Service:** BE-SVC-GSM · **Handler:** `TZ-Tigo-SuperApp-GSM/TZTigoSuperAppGSM/Controllers/GSMBundlesController.cs › GSMBundlesController.ProductProvision` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/GSMBundles/ProductProvision
  internal_path: /api/GSMBundles/ProductProvision
  dispatch_field: null
  dispatch_value: null
  controller_action: GSMBundlesController.ProductProvision
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** ProductProvisionRequest

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| consumerID | `string` | no | — | DataAnnotations / action | — |
| country | `string` | no | — | DataAnnotations / action | — |
| channelId | `string` | no | — | DataAnnotations / action | — |
| payingCustomerID | `string` | no | — | DataAnnotations / action | — |
| fulfillmentCustomerID | `string` | no | — | DataAnnotations / action | — |
| productId | `string` | no | — | DataAnnotations / action | — |
| desiredPaymentMethod | `string` | no | — | DataAnnotations / action | — |
| externalTransactionID | `string` | no | — | DataAnnotations / action | — |
| comment | `string` | no | — | DataAnnotations / action | — |
| additionalParameters | `List<ParameterType>` | no | — | DataAnnotations / action | — |
| parameterName | `string` | no | — | DataAnnotations / action | — |
| parameterValue | `string` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "consumerID": "<consumerID>", "country": "<country>", "channelId": "<channelId>", "payingCustomerID": "<payingCustomerID>", "fulfillmentCustomerID": "<fulfillmentCustomerID>", "productId": "<productId>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `GSMBundlesController.ProductProvision`
2. Action body in `TZTigoSuperAppGSM/Controllers/GSMBundlesController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as GSMBundlesController
  participant Svc as downstream
  App->>Ctrl: POST /api/GSMBundles/ProductProvision
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
- `TZ-Tigo-SuperApp-GSM/TZTigoSuperAppGSM/Controllers/GSMBundlesController.cs › GSMBundlesController.ProductProvision` @ `13fe724`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
