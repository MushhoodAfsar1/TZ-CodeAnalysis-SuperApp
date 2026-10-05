---
kb_section: backend
type: api-contract
ids: [BE-API-RESERV-005]
service: RESERV
repo: TZ-Tigo-SuperApp-Reservation
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: dfd072a
updated: 2026-10-05
confidence: confirmed
---
# BE-API-RESERV-005 BusTicketController.ProcessSeat
**Service:** BE-SVC-RESERV · **Handler:** `TZ-Tigo-SuperApp-Reservation/TZTigoSuperAppReservation/Controllers/BusTicketController.cs › BusTicketController.ProcessSeat` · **Conf.:** confirmed

## Match keys
```yaml
match_keys:
  public_method: POST
  public_path: /api/BusTicket
  internal_path: /api/BusTicket
  dispatch_field: null
  dispatch_value: null
  controller_action: BusTicketController.ProcessSeat
  topic: null
```

## Exposure & security
- **Auth:** none
- **Channel:** IDENT/SESS are portal or session APIs; mobile feature APIs typically use encrypted `payload` + `X-User-Session`.
- **Encryption filter:** ProcessSeatRequest

## Request (decrypted)
| Field (JSON) | Type | Req. | Format / length / enum | Enforced by | Meaning |
|---|---|---|---|---|---|
| payload | string | yes | AES-CBC Base64 of JSON | EncryptionProviderFilter | Encrypted body |
| SubId | `string` | no | — | DataAnnotations / action | — |
| TdiId | `string` | no | — | DataAnnotations / action | — |
| LbId | `string` | no | — | DataAnnotations / action | — |
| PbiId | `string` | no | — | DataAnnotations / action | — |
| AsiId | `string` | no | — | DataAnnotations / action | — |
| SeatId | `string` | no | — | DataAnnotations / action | — |
| Currency | `string?` | no | — | DataAnnotations / action | — |
| Ukey | `string` | no | — | DataAnnotations / action | — |
| FromId | `string` | no | — | DataAnnotations / action | — |
| ToId | `string` | no | — | DataAnnotations / action | — |
| TrvlDt | `string` | no | — | DataAnnotations / action | — |
| SeatTypeId | `string` | no | — | DataAnnotations / action | — |

Headers / route / query params:
- `X-User-Session` (Bearer JWT) when authenticated
- Content-Type: application/json

Sample (synthetic):
```json
{ "SubId": "<SubId>", "TdiId": "<TdiId>", "LbId": "<LbId>", "PbiId": "<PbiId>", "AsiId": "<AsiId>", "SeatId": "<SeatId>" }
```

## Checks & validations (execution order)
| # | Check | On failure | Rule ID | Evidence |
|---|---|---|---|---|


## Internal call chain
1. ASP.NET model binding (and EncryptionProviderFilter when present) → `BusTicketController.ProcessSeat`
2. Action body in `TZTigoSuperAppReservation/Controllers/BusTicketController.cs` (UserManager / services / DbContext as called)
3. Envelope returned (`BaseDto` / `BaseResponse` / `IActionResult`)

```mermaid
sequenceDiagram
  participant App
  participant Ctrl as BusTicketController
  participant Svc as downstream
  App->>Ctrl: POST /api/BusTicket
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
| See service data-model | R/W | Traced at SHA dfd072a |

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
See `services/reserv/business-rules.md`.

## Config keys
Names only: `TokenKey`, `isEncrypted` / `is_encrypted`, `Encryption_Decryption_Key`, `IV`, service-specific sections.

## Evidence
- `TZ-Tigo-SuperApp-Reservation/TZTigoSuperAppReservation/Controllers/BusTicketController.cs › BusTicketController.ProcessSeat` @ `dfd072a`

## Open questions
- Public gateway path may differ from controller route (no gateway repo in this set).
