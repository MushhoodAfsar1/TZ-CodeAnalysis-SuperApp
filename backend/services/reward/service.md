---
kb_section: backend
type: service
ids: [BE-SVC-REWARD]
service: REWARD
repo: TZ-Tigo-SuperApp-RewardReferral
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: b47cb93
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-REWARD TZ-Tigo-SuperApp-RewardReferral
**Repo:** `TZ-Tigo-SuperApp-RewardReferral` · **Type:** service · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `b47cb93`
**Purpose:** Rewards / referral

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-REWARD-001 | POST /api/RewardManagement | RewardManagementController.GenrateReferrelCode | — | none | confirmed |
| BE-API-REWARD-002 | POST /api/RewardManagement | RewardManagementController.RedeemReferrelCode | — | none | confirmed |
| BE-API-REWARD-003 | POST /api/RewardManagement | RewardManagementController.GetReferrelCodeById | — | none | confirmed |
| BE-API-REWARD-004 | POST /api/RewardManagement | RewardManagementController.GetAmount | — | none | confirmed |
| BE-API-REWARD-005 | POST /api/RewardManagement/encGenrateReferrelCode | RewardManagementController.encGenrateReferrelCode | — | none | confirmed |
| BE-API-REWARD-006 | POST /api/RewardManagement/decGenrateReferrelCode | RewardManagementController.decGenrateReferrelCode | — | none | confirmed |
| BE-API-REWARD-007 | POST /api/RewardManagement/encRedeemReferrelCode | RewardManagementController.encRedeemReferrelCode | — | none | confirmed |
| BE-API-REWARD-008 | POST /api/RewardManagement/decRedeemReferrelCode | RewardManagementController.decRedeemReferrelCode | — | none | confirmed |
| BE-API-REWARD-009 | POST /api/RewardManagement/enc | RewardManagementController.enc | — | none | confirmed |
| BE-API-REWARD-010 | POST /api/RewardManagement/dec | RewardManagementController.dec | — | none | confirmed |
| BE-API-REWARD-011 | POST /api/MixxPoints | MixxPointsController.GetPointsBalance | — | none | confirmed |
| BE-API-REWARD-012 | POST /api/MixxPoints | MixxPointsController.GetRewardProducts | — | none | confirmed |
| BE-API-REWARD-013 | POST /api/MixxPoints | MixxPointsController.RedeemPoints | — | none | confirmed |
| BE-API-REWARD-014 | POST /api/MixxPoints | MixxPointsController.GetRedemptionHistory | — | none | confirmed |
| BE-API-REWARD-015 | POST /api/MixxPoints/encGetPointsBalance | MixxPointsController.encGetPointsBalance | — | none | confirmed |
| BE-API-REWARD-016 | POST /api/MixxPoints/decGetPointsBalance | MixxPointsController.decGetPointsBalance | — | none | confirmed |
| BE-API-REWARD-017 | POST /api/MixxPoints/encGetRewardProducts | MixxPointsController.encGetRewardProducts | — | none | confirmed |
| BE-API-REWARD-018 | POST /api/MixxPoints/decGetRewardProducts | MixxPointsController.decGetRewardProducts | — | none | confirmed |
| BE-API-REWARD-019 | POST /api/MixxPoints/encRedeemPoints | MixxPointsController.encRedeemPoints | — | none | confirmed |
| BE-API-REWARD-020 | POST /api/MixxPoints/decRedeemPoints | MixxPointsController.decRedeemPoints | — | none | confirmed |
| BE-API-REWARD-021 | POST /api/MixxPoints/encGetRedemptionHistory | MixxPointsController.encGetRedemptionHistory | — | none | confirmed |
| BE-API-REWARD-022 | POST /api/MixxPoints/decGetRedemptionHistory | MixxPointsController.decGetRedemptionHistory | — | none | confirmed |


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
