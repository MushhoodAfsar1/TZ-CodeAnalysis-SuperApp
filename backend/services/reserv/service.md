---
kb_section: backend
type: service
ids: [BE-SVC-RESERV]
service: RESERV
repo: TZ-Tigo-SuperApp-Reservation
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: dfd072a
updated: 2026-10-05
confidence: confirmed
---

# BE-SVC-RESERV Movies and bus tickets
**Repo:** `TZ-Tigo-SuperApp-Reservation` · **Type:** service · **Stack:** net8.0 · **Ref/SHA:** `cursor/superapp-backend-documentation-cf53` / `dfd072a`
**Purpose:** Movies and bus tickets

## Exposure
ASP.NET Core controllers (`MapControllers`). No minimal APIs. See `overview/request-pipeline.md`.

**Packages (selected):** MassTransit.RabbitMQ, Microsoft.EntityFrameworkCore, Microsoft.EntityFrameworkCore.Tools, Npgsql.EntityFrameworkCore.PostgreSQL, Serilog.AspNetCore, Serilog.Filters.Expressions, Serilog.Formatting.Compact, StackExchange.Redis, Swashbuckle.AspNetCore

## APIs
| ID | Method + path | Controller.Action | Purpose | Auth | Conf. |
|---|---|---|---|---|---|
| BE-API-RESERV-001 | `POST /api/Movies/GetMovies` | `MoviesController.GetMovies` | MoviesController.GetMovies | see contract | confirmed |
| BE-API-RESERV-002 | `POST /api/Movies/GetSeatMap` | `MoviesController.GetSeatMap` | MoviesController.GetSeatMap | see contract | confirmed |
| BE-API-RESERV-003 | `POST /api/Movies/ReleaseSeats` | `MoviesController.ReleaseSeats` | MoviesController.ReleaseSeats | see contract | confirmed |
| BE-API-RESERV-004 | `POST /api/Movies/GetAvailableShows` | `MoviesController.GetAvailableShows` | MoviesController.GetAvailableShows | see contract | confirmed |
| BE-API-RESERV-005 | `POST /api/Movies/SeatSelection` | `MoviesController.SeatSelection` | MoviesController.SeatSelection | see contract | confirmed |
| BE-API-RESERV-006 | `POST /api/Movies/GetFare` | `MoviesController.GetFare` | MoviesController.GetFare | see contract | confirmed |
| BE-API-RESERV-007 | `POST /api/Movies/BookMovieSeat` | `MoviesController.BookMovieSeat` | MoviesController.BookMovieSeat | see contract | confirmed |
| BE-API-RESERV-008 | `POST /api/BusTicket/GetStations` | `BusTicketController.GetStations` | BusTicketController.GetStations | see contract | confirmed |
| BE-API-RESERV-009 | `POST /api/BusTicket/SearchBuses` | `BusTicketController.SearchBuses` | BusTicketController.SearchBuses | see contract | confirmed |
| BE-API-RESERV-010 | `POST /api/BusTicket/GetFare` | `BusTicketController.GetFare` | BusTicketController.GetFare | see contract | confirmed |
| BE-API-RESERV-011 | `POST /api/BusTicket/SeatMapping` | `BusTicketController.SeatMapping` | BusTicketController.SeatMapping | see contract | confirmed |
| BE-API-RESERV-012 | `POST /api/BusTicket/ProcessSeat` | `BusTicketController.ProcessSeat` | BusTicketController.ProcessSeat | see contract | confirmed |
| BE-API-RESERV-013 | `POST /api/BusTicket/ReserveBooking` | `BusTicketController.ReserveBooking` | BusTicketController.ReserveBooking | see contract | confirmed |

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
| `ReservationPayments` / `ReservationPayments` | EF set |
| `BusTicketRecords` / `BusTicketRecords` | EF set |
| `MovieTicketRecords` / `MovieTicketRecords` | EF set |

## Events · Jobs · Integrations (links)
- [events.md](events.md) · [jobs.md](jobs.md) · [integrations.md](integrations.md)

## Config keys that change behaviour (names only)
`BusTicketing:Currency`, `BusTicketing:GetFare`, `BusTicketing:GetStations`, `BusTicketing:PayCode`, `BusTicketing:ProcessSeat`, `BusTicketing:ReserveBooking`, `BusTicketing:SearchBuses`, `BusTicketing:SeatMapping`, `BusTicketing:TargetMSISDN`, `BusTicketing:agent_id`, `BusTicketing:app_ver`, `BusTicketing:auth_key`, `BusTicketing:is_from_android`, `BusTicketing:is_from_ios`, `BusTicketing:langEN`, `BusTicketing:langSW`, `BusTicketing:pltfm`, `EnableLog:Debug`, `EnableLog:Error`, `EnableLog:Information`, `Encryption_Decryption_Key`, `FCMNotify`, `IV`, `MovieTicketing:BookSeat`, `MovieTicketing:GetAvailableShows`, `MovieTicketing:GetFare`, `MovieTicketing:GetMovies`, `MovieTicketing:ReleaseSeats`, `MovieTicketing:SeatMap`, `MovieTicketing:SeatSelection`, `MovieTicketing:TargetMSISDN`, `MovieTicketing:app_ver`, `MovieTicketing:auid`, `MovieTicketing:ext_tran_id`, `MovieTicketing:is_from`, `MovieTicketing:langEN`, `MovieTicketing:langSW`, `MovieTicketing:pay_code`, `MovieTicketing:pay_phone`, `MovieTicketing:phone_no`

## Open questions
- Gateway public URLs not in-repo.
