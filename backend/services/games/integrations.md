---
kb_section: backend
type: service
ids: [BE-SVC-GAMES]
service: GAMES
repo: TZ-Tigo-SuperApp-Games
repo_ref: cursor/superapp-backend-documentation-cf53
repo_sha: 10c8daa
updated: 2026-10-05
confidence: partial
---

# Integrations — GAMES

Hosts/secrets omitted.

| ID | Name | How | Evidence |
|---|---|---|---|
| BE-INT-GAMES-001 | HttpClient `CMM` | named client; base URL from config key (value omitted) | Program/DI |
| BE-INT-GAMES-002 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}` | outbound HTTP path shape | static string |
| BE-INT-GAMES-003 | `api/ResponseCodeApp/get-response-code-details/{responseCode}/{language}/{channel}/{service}/{serviceMethod}` | outbound HTTP path shape | static string |
