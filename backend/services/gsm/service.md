---
kb_section: backend
type: service
ids: [BE-SVC-GSM]
service: GSM
repo: TZ-Tigo-SuperApp-GSM
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 13fe724
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-GSM TZ-Tigo-SuperApp-GSM
**Repo:** `TZ-Tigo-SuperApp-GSM` · **Type:** service · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `13fe724`
**Purpose:** GSM / SIM

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-GSM-001 | POST /api/SelfCare/InternetSetting | SelfCareController.InternetSetting | — | none | confirmed |
| BE-API-GSM-002 | POST /api/SelfCare/GetPuk | SelfCareController.GetPuk | — | none | confirmed |
| BE-API-GSM-003 | POST /api/SelfCare/GetDataUsage | SelfCareController.GetDataUsage | — | none | confirmed |
| BE-API-GSM-004 | POST /api/SelfCare/GetAvailableData | SelfCareController.GetAvailableData | — | none | confirmed |
| BE-API-GSM-005 | POST /api/SelfCare/ShareData | SelfCareController.ShareData | — | none | confirmed |
| BE-API-GSM-006 | POST /api/SelfCare/enc | SelfCareController.enc | — | none | confirmed |
| BE-API-GSM-007 | POST /api/GSMBundles/CheckBalanceAirtimeSmsAndCall | GSMBundlesController.CheckBalanceAirtimeSmsAndCall | — | none | confirmed |
| BE-API-GSM-008 | POST /api/GSMBundles/HomeInternet | GSMBundlesController.HomeInternet | — | none | confirmed |
| BE-API-GSM-009 | POST /api/GSMBundles/ProductProvision | GSMBundlesController.ProductProvision | — | none | confirmed |
| BE-API-GSM-010 | POST /api/GSMBundles/SuperAppGetSubscriberInfo | GSMBundlesController.SuperAppGetSubscriberInfo | — | none | confirmed |
| BE-API-GSM-011 | POST /api/GSMBundles/CheckBalanceAirtimeSmsAndCallV2 | GSMBundlesController.CheckBalanceAirtimeSmsAndCallV2 | — | none | confirmed |
| BE-API-GSM-012 | POST /api/GSMBundles/HomeInternetV2 | GSMBundlesController.HomeInternetV2 | — | none | confirmed |
| BE-API-GSM-013 | POST /api/GSMBundles/ProductProvisionV2 | GSMBundlesController.ProductProvisionV2 | — | none | confirmed |
| BE-API-GSM-014 | POST /api/GSMBundles/SuperAppGetSubscriberInfoV2 | GSMBundlesController.SuperAppGetSubscriberInfoV2 | — | none | confirmed |
| BE-API-GSM-015 | POST /api/GSMBundles/encrypt | GSMBundlesController.Encrypt | — | none | confirmed |
| BE-API-GSM-016 | POST /api/GSMBundles/decrypt | GSMBundlesController.Decrypt | — | none | confirmed |


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
Status this run: **deep-analyzed**
