---
kb_section: backend
type: service
ids: [BE-SVC-REWARD]
service: REWARD
repo: TZ-Tigo-SuperApp-RewardReferral
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: b47cb93
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-REWARD Mixx points and referral rewards
**Repo:** `TZ-Tigo-SuperApp-RewardReferral` · **Type:** service · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `b47cb93`
**Purpose:** Mixx points and referral rewards

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** MassTransit.RabbitMQ, Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-REWARD-001 | `POST /api/RewardManagement/GenrateReferrelCode` | `RewardManagementController.GenrateReferrelCode` | RewardManagementController.GenrateReferrelCode | see contract | confirmed |
| BE-API-REWARD-002 | `POST /api/RewardManagement/RedeemReferrelCode` | `RewardManagementController.RedeemReferrelCode` | RewardManagementController.RedeemReferrelCode | see contract | confirmed |
| BE-API-REWARD-003 | `POST /api/RewardManagement/GetReferrelCodeById` | `RewardManagementController.GetReferrelCodeById` | RewardManagementController.GetReferrelCodeById | see contract | confirmed |
| BE-API-REWARD-004 | `POST /api/RewardManagement/GetAmount` | `RewardManagementController.GetAmount` | RewardManagementController.GetAmount | see contract | confirmed |
| BE-API-REWARD-005 | `POST /api/RewardManagement/encGenrateReferrelCode` | `RewardManagementController.encGenrateReferrelCode` | RewardManagementController.encGenrateReferrelCode | see contract | confirmed |
| BE-API-REWARD-006 | `POST /api/RewardManagement/decGenrateReferrelCode` | `RewardManagementController.decGenrateReferrelCode` | RewardManagementController.decGenrateReferrelCode | see contract | partial |
| BE-API-REWARD-007 | `POST /api/RewardManagement/encRedeemReferrelCode` | `RewardManagementController.encRedeemReferrelCode` | RewardManagementController.encRedeemReferrelCode | see contract | confirmed |
| BE-API-REWARD-008 | `POST /api/RewardManagement/decRedeemReferrelCode` | `RewardManagementController.decRedeemReferrelCode` | RewardManagementController.decRedeemReferrelCode | see contract | partial |
| BE-API-REWARD-009 | `POST /api/RewardManagement/enc` | `RewardManagementController.enc` | RewardManagementController.enc | see contract | confirmed |
| BE-API-REWARD-010 | `POST /api/RewardManagement/dec` | `RewardManagementController.dec` | RewardManagementController.dec | see contract | partial |
| BE-API-REWARD-011 | `POST /api/MixxPoints/GetPointsBalance` | `MixxPointsController.GetPointsBalance` | MixxPointsController.GetPointsBalance | see contract | confirmed |
| BE-API-REWARD-012 | `POST /api/MixxPoints/GetRewardProducts` | `MixxPointsController.GetRewardProducts` | MixxPointsController.GetRewardProducts | see contract | confirmed |
| BE-API-REWARD-013 | `POST /api/MixxPoints/RedeemPoints` | `MixxPointsController.RedeemPoints` | MixxPointsController.RedeemPoints | see contract | confirmed |
| BE-API-REWARD-014 | `POST /api/MixxPoints/GetRedemptionHistory` | `MixxPointsController.GetRedemptionHistory` | MixxPointsController.GetRedemptionHistory | see contract | confirmed |
| BE-API-REWARD-015 | `POST /api/MixxPoints/encGetPointsBalance` | `MixxPointsController.encGetPointsBalance` | MixxPointsController.encGetPointsBalance | see contract | confirmed |
| BE-API-REWARD-016 | `POST /api/MixxPoints/decGetPointsBalance` | `MixxPointsController.decGetPointsBalance` | MixxPointsController.decGetPointsBalance | see contract | partial |
| BE-API-REWARD-017 | `POST /api/MixxPoints/encGetRewardProducts` | `MixxPointsController.encGetRewardProducts` | MixxPointsController.encGetRewardProducts | see contract | confirmed |
| BE-API-REWARD-018 | `POST /api/MixxPoints/decGetRewardProducts` | `MixxPointsController.decGetRewardProducts` | MixxPointsController.decGetRewardProducts | see contract | partial |
| BE-API-REWARD-019 | `POST /api/MixxPoints/encRedeemPoints` | `MixxPointsController.encRedeemPoints` | MixxPointsController.encRedeemPoints | see contract | confirmed |
| BE-API-REWARD-020 | `POST /api/MixxPoints/decRedeemPoints` | `MixxPointsController.decRedeemPoints` | MixxPointsController.decRedeemPoints | see contract | partial |
| BE-API-REWARD-021 | `POST /api/MixxPoints/encGetRedemptionHistory` | `MixxPointsController.encGetRedemptionHistory` | MixxPointsController.encGetRedemptionHistory | see contract | confirmed |
| BE-API-REWARD-022 | `POST /api/MixxPoints/decGetRedemptionHistory` | `MixxPointsController.decGetRedemptionHistory` | MixxPointsController.decGetRedemptionHistory | see contract | partial |

## Dependencies
| Calls | Sync/Async | Why |
|---|---|---|
| CONFIG `CMM` / `ConfigAPIUrl` | Sync | response-code mapping, catalogues |

| Called by | Sync/Async | Why |
|---|---|---|
| Mobile app (direct or via external gateway) | Sync | product APIs |
| WebPortal | Sync | admin screens (IDENT/CONFIG mainly) |

## Data owned
| Entity / table | Purpose |
|---|---|
| `BaseEntity` / `—` | `TZTigoSuperAppRewardReferral/Data/Entities/BaseEntity.cs` |
| `ReferralBonusType` / `—` | `TZTigoSuperAppRewardReferral/Domain/Enumerators/ReferralBonusType.cs` |
| `SubscriptionRepository` / `—` | `TZTigoSuperAppRewardReferral/Domain/Repositories/SubscriptionRepository.cs` |
| `ReferrelCodeRepository` / `—` | `TZTigoSuperAppRewardReferral/Domain/Repositories/ReferrelCodeRepository.cs` |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`ConfigAPIUrl`, `DeepLinkInfo:APIKey`, `DeepLinkInfo:AndriodStoreLink`, `DeepLinkInfo:AndroidPackageName`, `DeepLinkInfo:DomainUriPrefix`, `DeepLinkInfo:FirebaseDynamicBaseLink`, `DeepLinkInfo:IOSBundleId`, `DeepLinkInfo:IosStoreLink`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `EnableLog:Warning`, `Encryption_Decryption_Key`, `IV`, `IsRedisCluster`, `LoginURL`, `MFSUserDetails`, `MixxPoints`, `Origins`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:LogQueueName`, `RabbitMQ:LogURL`, `RabbitMQ:Username`, `RedisPassword (key name)<redacted-purpose>`, `RedisURL`, `SaveLogs`, `SendAuditLogsViaService`, `SubscriptionStatus`, `Tanzania:<redacted-purpose>`, `Tanzania:Account:UserName`, `Tanzania:ConsumerID`, `Tanzania:Login:Username`, `Tanzania:Login:consumerID`, `Tanzania:MTPGPaymentRequest:ConsumerID`, `Tanzania:MTPGPaymentRequest:ShortCode`, `Tanzania:MTPGPaymentRequest:SuperAppMTPGPaymentURI`, `Tanzania:Subscription`, `Tanzania:Withdraw`, `Tanzania:responseChanel`, `Tanzania:serviceName`

## Open questions
- Gateway public URLs not in-repo.
