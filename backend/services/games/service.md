---
kb_section: backend
type: service
ids: [BE-SVC-GAMES]
service: GAMES
repo: TZ-Tigo-SuperApp-Games
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: 10c8daa
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-GAMES TZ-Tigo-SuperApp-Games
**Repo:** `TZ-Tigo-SuperApp-Games` · **Type:** service · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `10c8daa`
**Purpose:** Games

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-GAMES-001 | POST /api/FifaGames/CheckFavoriteTeam | FifaGamesController.CheckFavoriteTeam | — | none | confirmed |
| BE-API-GAMES-002 | POST /api/FifaGames/ListTeams | FifaGamesController.ListTeams | — | none | confirmed |
| BE-API-GAMES-003 | POST /api/FifaGames/SaveFavoriteTeam | FifaGamesController.SaveFavoriteTeam | — | none | confirmed |
| BE-API-GAMES-004 | POST /api/FifaGames/UpdateFavoriteTeam | FifaGamesController.UpdateFavoriteTeam | — | none | confirmed |
| BE-API-GAMES-005 | POST /api/FifaGames/ListFixtures | FifaGamesController.ListFixtures | — | none | confirmed |
| BE-API-GAMES-006 | POST /api/FifaGames/GetLiveMatches | FifaGamesController.GetLiveMatches | — | none | confirmed |
| BE-API-GAMES-007 | POST /api/FifaGames/GetRewardBalance | FifaGamesController.GetRewardBalance | — | none | confirmed |
| BE-API-GAMES-008 | POST /api/FifaGames/RedeemRewards | FifaGamesController.RedeemRewards | — | none | confirmed |


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
