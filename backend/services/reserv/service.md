---
kb_section: backend
type: service
ids: [BE-SVC-RESERV]
service: RESERV
repo: TZ-Tigo-SuperApp-Reservation
repo_ref: cursor/superapp-backend-documentation-6fa7
repo_sha: dfd072a
updated: 2026-10-05
confidence: confirmed
---
# BE-SVC-RESERV TZ-Tigo-SuperApp-Reservation
**Repo:** `TZ-Tigo-SuperApp-Reservation` · **Type:** service · **Stack:** ASP.NET Core net8.0 (PORTAL: Angular) · **Ref/SHA:** `dfd072a`
**Purpose:** Reservations

## Exposure
HTTP controllers under the service project. Scheduler repos expose hosted jobs instead of HTTP.

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-RESERV-001 | POST /api/BusTicket | BusTicketController.GetStations | — | none | confirmed |
| BE-API-RESERV-002 | POST /api/BusTicket | BusTicketController.SearchBuses | — | none | confirmed |
| BE-API-RESERV-003 | POST /api/BusTicket | BusTicketController.GetFare | — | none | confirmed |
| BE-API-RESERV-004 | POST /api/BusTicket | BusTicketController.SeatMapping | — | none | confirmed |
| BE-API-RESERV-005 | POST /api/BusTicket | BusTicketController.ProcessSeat | — | none | confirmed |
| BE-API-RESERV-006 | POST /api/BusTicket | BusTicketController.ReserveBooking | — | none | confirmed |
| BE-API-RESERV-007 | POST /api/Movies | MoviesController.GetMovies | — | none | confirmed |
| BE-API-RESERV-008 | POST /api/Movies | MoviesController.GetSeatMap | — | none | confirmed |
| BE-API-RESERV-009 | POST /api/Movies | MoviesController.ReleaseSeats | — | none | confirmed |
| BE-API-RESERV-010 | POST /api/Movies | MoviesController.GetAvailableShows | — | none | confirmed |
| BE-API-RESERV-011 | POST /api/Movies | MoviesController.SeatSelection | — | none | confirmed |
| BE-API-RESERV-012 | POST /api/Movies | MoviesController.GetFare | — | none | confirmed |
| BE-API-RESERV-013 | POST /api/Movies | MoviesController.BookMovieSeat | — | none | confirmed |


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
