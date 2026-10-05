---
kb_section: backend
type: api-contract
ids: [BE-API-CONFIG-351]
service: CONFIG
repo: TZ-Tigo-SuperApp-Configuration
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 9c00072
updated: 2026-10-05
confidence: confirmed
---
# BE-API-CONFIG-351 BundlesAppController.GetSeziakoBundles
**Service:** BE-SVC-CONFIG · **Handler:** `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/BundlesAppController.cs › BundlesAppController.GetSeziakoBundles` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/BundlesApp/GetSeziakoBundles
  internal_path: /api/BundlesApp/GetSeziakoBundles
  dispatch_field: null
  dispatch_value: null
  controller_action: BundlesAppController.GetSeziakoBundles
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** BundlesRequest

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| msisdn | `string` | no | — | DataAnnotations / action | — |
| targetmsisdn | `string` | no | — | DataAnnotations / action | — |
| languageId | `string` | no | — | DataAnnotations / action | — |
| transactionId | `string` | no | — | DataAnnotations / action | — |
| operatorType | `string` | no | — | DataAnnotations / action | — |
| msisdn | `string` | no | — | DataAnnotations / action | — |
| targetmsisdn | `string` | no | — | DataAnnotations / action | — |
| languageId | `string` | no | — | DataAnnotations / action | — |
| transactionId | `string` | no | — | DataAnnotations / action | — |
| operatorType | `string` | no | — | DataAnnotations / action | — |
| recommendations | `Recommendations` | no | — | DataAnnotations / action | — |
| status | `string` | no | — | DataAnnotations / action | — |
| msisdn | `string` | no | — | DataAnnotations / action | — |
| transactionId | `string` | no | — | DataAnnotations / action | — |
| product | `List<Product>` | no | — | DataAnnotations / action | — |
| order | `string` | no | — | DataAnnotations / action | — |
| productDetails | `ProductDetails` | no | — | DataAnnotations / action | — |
| cBSAppendantId | `string` | no | — | DataAnnotations / action | — |
| type | `string` | no | — | DataAnnotations / action | — |
| name | `string` | no | — | DataAnnotations / action | — |
| validity | `string` | no | — | DataAnnotations / action | — |
| details | `string` | no | — | DataAnnotations / action | — |
| fullfillmentId | `FullfillmentId` | no | — | DataAnnotations / action | — |
| tPesa | `string` | no | — | DataAnnotations / action | — |
| cbs | `string` | no | — | DataAnnotations / action | — |
| recommendations | `string` | no | — | DataAnnotations / action | — |
| status | `string` | no | — | DataAnnotations / action | — |
| msisdn | `string` | no | — | DataAnnotations / action | — |
| transactionId | `string` | no | — | DataAnnotations / action | — |
| product | `string` | no | — | DataAnnotations / action | — |
| order | `string` | no | — | DataAnnotations / action | — |
| productDetails | `string` | no | — | DataAnnotations / action | — |
| cbsAppendantId | `string` | no | — | DataAnnotations / action | — |
| type | `string` | no | — | DataAnnotations / action | — |
| name | `string` | no | — | DataAnnotations / action | — |
| validity | `string` | no | — | DataAnnotations / action | — |
| details | `string` | no | — | DataAnnotations / action | — |
| fullfillmentId | `string` | no | — | DataAnnotations / action | — |
| tpesa | `string` | no | — | DataAnnotations / action | — |
| cbs | `string` | no | — | DataAnnotations / action | — |
| id | `int` | no | — | DataAnnotations / action | — |
| engCategory | `string?` | no | — | DataAnnotations / action | — |
| swCategory | `string?` | no | — | DataAnnotations / action | — |
| enPackName | `string?` | no | — | DataAnnotations / action | — |
| swPackName | `string?` | no | — | DataAnnotations / action | — |
| productId | `string?` | no | — | DataAnnotations / action | — |
| ffeId | `string?` | no | — | DataAnnotations / action | — |
| engValidity | `string?` | no | — | DataAnnotations / action | — |
| swValidity | `string?` | no | — | DataAnnotations / action | — |
| data | `string?` | no | — | DataAnnotations / action | — |
| price | `string?` | no | — | DataAnnotations / action | — |
| engDescription | `string?` | no | — | DataAnnotations / action | — |
| swDescription | `string?` | no | — | DataAnnotations / action | — |
| simCategory | `bool?` | no | — | DataAnnotations / action | — |
| id | `int` | no | — | DataAnnotations / action | — |
| category | `string?` | no | — | DataAnnotations / action | — |
| type | `string?` | no | — | DataAnnotations / action | — |
| action | `string?` | no | — | DataAnnotations / action | — |
| price | `string?` | no | — | DataAnnotations / action | — |
| levelIDisplay | `string?` | no | — | DataAnnotations / action | — |
| levelIIDisplay | `string?` | no | — | DataAnnotations / action | — |
| tpProductId | `string?` | no | — | DataAnnotations / action | — |
| cbsProductId | `string?` | no | — | DataAnnotations / action | — |
| tpFfeId | `string?` | no | — | DataAnnotations / action | — |
| giftFfeId | `string?` | no | — | DataAnnotations / action | — |
| cbsFfeId | `string?` | no | — | DataAnnotations / action | — |
| subscriber | `string?` | no | — | DataAnnotations / action | — |
| request | `PelatroRequest` | no | — | DataAnnotations / action | — |
| msisdn | `string` | no | — | DataAnnotations / action | — |
| transactionId | `string` | no | — | DataAnnotations / action | — |
| language | `string` | no | — | DataAnnotations / action | — |
| channel | `string` | no | — | DataAnnotations / action | — |
| response | `PelatroResponse` | no | — | DataAnnotations / action | — |
| recommendations | `PelatroRecommendations` | no | — | DataAnnotations / action | — |
| status | `string` | no | — | DataAnnotations / action | — |
| msisdn | `string` | no | — | DataAnnotations / action | — |
| transactionId | `string` | no | — | DataAnnotations / action | — |
| metadata | `PelatroMetadata` | no | — | DataAnnotations / action | — |
| staticProducts | `List<PelatroStaticProduct>` | no | — | DataAnnotations / action | — |
| locationProducts | `List<PelatroLocationProduct>` | no | — | DataAnnotations / action | — |
| order | `int` | no | — | DataAnnotations / action | — |
| productId | `string` | no | — | DataAnnotations / action | — |
| productDetails | `PelatroProductDetails` | no | — | DataAnnotations / action | — |
| order | `int` | no | — | DataAnnotations / action | — |
| productId | `string` | no | — | DataAnnotations / action | — |
| productDetails | `PelatroProductDetails` | no | — | DataAnnotations / action | — |
| type | `string` | no | — | DataAnnotations / action | — |
| name | `string` | no | — | DataAnnotations / action | — |
| validity | `string` | no | — | DataAnnotations / action | — |
| details | `string` | no | — | DataAnnotations / action | — |
| fulfillmentId | `PelatroFulfillmentId` | no | — | DataAnnotations / action | — |
| mfs | `string` | no | — | DataAnnotations / action | — |
| cbs | `string` | no | — | DataAnnotations / action | — |
| totalOffers | `int` | no | — | DataAnnotations / action | — |
| staticOffers | `int` | no | — | DataAnnotations / action | — |
| locationOffers | `int` | no | — | DataAnnotations / action | — |
| language | `string` | no | — | DataAnnotations / action | — |
| channel | `string` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "msisdn": "<msisdn>", "targetmsisdn": "<targetmsisdn>", "languageId": "<languageId>", "transactionId": "<transactionId>", "operatorType": "<operatorType>", "msisdn": "<msisdn>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `BundlesAppController.GetSeziakoBundles`
2. Action body in `TZTigoSuperAppConfiguration/Controllers/AppController/BundlesAppController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as BundlesAppController
  participant Svc as downstream
  App->>Ctrl: POST /api/BundlesApp/GetSeziakoBundles
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
| See service data-model | R/W | Traced at SHA 9c00072 |

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
See `services/config/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Configuration/TZTigoSuperAppConfiguration/Controllers/AppController/BundlesAppController.cs › BundlesAppController.GetSeziakoBundles` @ `9c00072`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
