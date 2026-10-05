---
kb_section: backend
type: service
ids: [BE-SVC-VCARD]
service: VCARD
repo: TZ-Tigo-SuperApp-VirtualCard
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: db358e6
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-VCARD TZ-Tigo-SuperApp-VirtualCard
**Repo:** `TZ-Tigo-SuperApp-VirtualCard` · **Type:** service · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `db358e6`
**Purpose:** Virtual cards

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-VCARD-001 | POST /api/CardManagement | CardManagementController.GetCardList | — | none | confirmed |
| BE-API-VCARD-002 | POST /api/CardManagement | CardManagementController.GetCardValidity | — | none | confirmed |
| BE-API-VCARD-003 | POST /api/CardManagement | CardManagementController.CreateMasterCard | — | none | confirmed |
| BE-API-VCARD-004 | POST /api/CardManagement | CardManagementController.GetCardTransaction | — | none | confirmed |
| BE-API-VCARD-005 | POST /api/CardManagement | CardManagementController.GetCardDetail | — | none | confirmed |
| BE-API-VCARD-006 | POST /api/CardManagement | CardManagementController.EnableDisableCard | — | none | confirmed |
| BE-API-VCARD-007 | POST /api/CardManagement | CardManagementController.DeleteCard | — | none | confirmed |
| BE-API-VCARD-008 | POST /api/CardManagement | CardManagementController.GetValidityDays | — | none | confirmed |
| BE-API-VCARD-009 | POST /api/CardManagement/enc | CardManagementController.enc | — | none | confirmed |


## Dependencies
| Calls | Sync/Async | Why |
|---|---|---|
| Session / Account / Config (typical) | Sync HTTP | Token and profile checks |
| Called by | Sync/Async | Why |
| Mobile app / portal | Sync | User journeys |

## Data owned
| Entity / table | Purpose |
|---|---|
| See data-model.md | — |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`TokenKey`, `isEncrypted`/`is_encrypted`, `Encryption_Decryption_Key`, `IV`, `JwtExpiryMins`, `PostgresConnection` (name only)

## Open questions
Status this run: **inventoried**
