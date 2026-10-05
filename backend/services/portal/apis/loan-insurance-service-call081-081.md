---
kb_section: backend
type: api-contract
ids: [BE-API-PORTAL-081]
service: PORTAL
repo: TZ-Tigo-SuperApp-WebPortal
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: bb69e15
updated: 2026-10-05
confidence: confirmed
---

# BE-API-PORTAL-081 loan-insurance.service.call081
**Service:** BE-SVC-PORTAL · **Handler:** `TZ-Tigo-SuperApp-WebPortal/src/app/services/loan-insurance.service.ts › loan-insurance.service.call081` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: {literal}${this.baseUrl}/loanprotect/save
  internal_path: {literal}${this.baseUrl}/loanprotect/save
  dispatch_field: null
  dispatch_value: null
  controller_action: loan-insurance.service.call081
  topic: null
```

## Exposure & security
- **Method / path:** `POST {literal}${this.baseUrl}/loanprotect/save`
- **Auth / filters:** Authorize (JWT) + AuthorizationFilter (CONFIG BO) or portal session header `X-User-Session`
- **Encryption:** Identity/CONFIG portal APIs are not payload-AES; mobile feature APIs are (see overview).

## Request (decrypted)
Angular `loan-insurance.service` calls CONFIG/IDENT/NOTIF/MCHANGO using environment **key names** `authApiUrl`, `configurationApiUrl`, `notificationUrl`, `mchangoUrl` (hosts omitted). Relative suffix: `{literal}${this.baseUrl}/loanprotect/save`.


Sample (synthetic):
```json
{}
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|
| 1 | JWT / AuthorizationFilter `Controller:Action` claim | 401/403 | BE-BR-PORTAL-001 | `TZ-Tigo-SuperApp-WebPortal/src/app/services/loan-insurance.service.ts › loan-insurance.service.call081` |

## Internal call chain
1. `loan-insurance.service.call081` at `TZ-Tigo-SuperApp-WebPortal/src/app/services/loan-insurance.service.ts`.
2. Repository / EF / Firebase client as implemented in the action body.

```mermaid
sequenceDiagram
  participant Portal
  participant loan-insurance.service
  Portal->>loan-insurance.service: POST {literal}${this.baseUrl}/loanprotect/save
  loan-insurance.service->>Portal: ActionResult
```

## Downstream
| Order | Target (BE-API / BE-INT / BE-EVT) | Sync/Async | Condition | Sent / used fields |
|---|---|---|---|---|
| — | in-process CONFIG/IDENT data stores | Sync | always | — |

## Data touched
| Entity / table / SP | R/W | Notes |
|---|---|---|
| see service data-model | mixed | |

## Response (decrypted)
| Field (JSON) | Type | Always / when | Meaning |
|---|---|---|---|
| body | ActionResult | always | ASP.NET result / BaseDto |

Sample (synthetic):
```json
{ "success": true, "responseData": {} }
```

## Errors
| BE code | HTTP | ID | Condition | Message key/text | Retryable |
|---|---|---|---|---|---|
| 401/403 | 401/403 | BE-ERR-PORTAL-003 | missing/invalid JWT | ASP.NET challenge | no |

## Side effects
## Business rules (links)
## Config keys
## Evidence
- `TZ-Tigo-SuperApp-WebPortal/src/app/services/loan-insurance.service.ts › loan-insurance.service.call081` @ `bb69e15`

## Open questions
- Public gateway prefix not in this repo.
