---
kb_section: backend
type: service
ids: [BE-SVC-GAMES]
service: GAMES
repo: TZ-Tigo-SuperApp-Games
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 10c8daa
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-GAMES Games
**Repo:** `TZ-Tigo-SuperApp-Games` · **Type:** service · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `10c8daa`
**Purpose:** Games

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, RabbitMQ.Client, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-GAMES-001 | `POST /api/FifaGames/CheckFavoriteTeam` | `FifaGamesController.CheckFavoriteTeam` | FifaGamesController.CheckFavoriteTeam | see contract | confirmed |
| BE-API-GAMES-002 | `POST /api/FifaGames/ListTeams` | `FifaGamesController.ListTeams` | FifaGamesController.ListTeams | see contract | confirmed |
| BE-API-GAMES-003 | `POST /api/FifaGames/SaveFavoriteTeam` | `FifaGamesController.SaveFavoriteTeam` | FifaGamesController.SaveFavoriteTeam | see contract | confirmed |
| BE-API-GAMES-004 | `POST /api/FifaGames/UpdateFavoriteTeam` | `FifaGamesController.UpdateFavoriteTeam` | FifaGamesController.UpdateFavoriteTeam | see contract | confirmed |
| BE-API-GAMES-005 | `POST /api/FifaGames/ListFixtures` | `FifaGamesController.ListFixtures` | FifaGamesController.ListFixtures | see contract | confirmed |
| BE-API-GAMES-006 | `POST /api/FifaGames/GetLiveMatches` | `FifaGamesController.GetLiveMatches` | FifaGamesController.GetLiveMatches | see contract | confirmed |
| BE-API-GAMES-007 | `POST /api/FifaGames/GetRewardBalance` | `FifaGamesController.GetRewardBalance` | FifaGamesController.GetRewardBalance | see contract | confirmed |
| BE-API-GAMES-008 | `POST /api/FifaGames/RedeemRewards` | `FifaGamesController.RedeemRewards` | FifaGamesController.RedeemRewards | see contract | confirmed |

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
| `FavTeamRegistration` / `FavTeamRegistrations` | EF set |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`AzureBlobStorage:<redacted-purpose>`, `AzureBlobStorage:DiasporaContainer`, `ConfigAPIUrl`, `DBServerUrl`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `EnableLog:Warning`, `Encryption_Decryption_Key`, `FCMNotify`, `FifaApi:<redacted-purpose>`, `FifaApi:ApiKey`, `FifaApi:CheckFavTeamUrl`, `FifaApi:ListFixturesUrl`, `FifaApi:ListTeamsUrl`, `FifaApi:LiveMatchesUrl`, `FifaApi:RedeemRewardsUrl`, `FifaApi:RewardBalanceUrl`, `FifaApi:SaveFavTeamUrl`, `FifaApi:TokenUrl`, `FifaApi:UpdateFavTeamUrl`, `IV`, `IsRedisCluster`, `RabbitMQ:<redacted-purpose>`, `RabbitMQ:LogQueueName`, `RabbitMQ:LogURL`, `RabbitMQ:QueueName`, `RabbitMQ:Username`, `RedisPassword (key name)<redacted-purpose>`, `RedisURL`, `SaveLogs`, `SendAuditLogsViaService`, `SendFCMViaService`, `Tanzania:responseChanel`, `TempServerUrl`, `TokenKey`, `UploadOnAzureStorage`, `is_encrypted`, `responseChanel`, `serviceName`

## Open questions
- Gateway public URLs not in-repo.
